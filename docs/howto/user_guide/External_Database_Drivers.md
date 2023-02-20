##### Chapter 12-7
##### External Database Drivers

This chapter describes how to write a Domino database driver. A database driver allows a Domino or Notes user to read data from a non-Domino database by calling the functions @DbLookup and @DbColumn. Before reading this chapter, you should have a good understanding of the user-level functionality and syntax of the @DbLookup and @DbColumn functions, as described in the <i>Domino 7.0 Designer Help </i>documentation.<br>
<br>
The code in this chapter is intended as a general illustration of the ideas discussed. For a more detailed look at a simple database driver, see the sample program samples\misc\dbdrive.<br>
<br>
<br>
<b><font size="5" color="#000080">Background</font></b><br>
<br>
The Domino Designer functions, @DbLookup and @DbColumn, are basically context-free, to keep their syntax simple. That is, the user is never asked to &quot;Open&quot; or &quot;Close&quot; a database in formulas that use these functions; furthermore, they are executed in such rapid succession that caching must be implemented at several levels to gain any efficiency.<br>
<br>
The highest layer of caching, Query/Result caching, is performed above the level of the database driver. For the most part, the semantics of the @DbLookup and @DbColumn functions mean that the higher-level caching is transparent to the driver, so it is not discussed in this chapter.<br>
<br>
The other layer of caching, open database session management, is performed by the driver in cooperation with the higher layer of software, the Database Driver Manager.  This manager is responsible for taking database @Function requests from the Formula Evaluator, parsing out the database driver name (in the first argument), loading the driver into the process's address space and initializing it if not already loaded, opening and managing sessions to the driver, and finally issuing the Function requests to the driver itself.<br>
<br>
The driver itself has two principal responsibilities:  managing &quot;sessions&quot; with the outside world and performing Functions on a session as requested.  The following explains the various driver functions in more detail and provides some skeleton subroutines to use as a guide.<br>
<br>
<br>
<b><font size="5" color="#000080">Database Driver Packaging and Concurrency Requirements</font></b>
<ul></ul>
As in all Domino and Notes low-level subsystems, database drivers must obey strict rules to fit into their computing environment:
<ul></ul>

<ol type="1">
<li>The drivers are packaged as executable program libraries (Dynamic Link Libraries under Windows, shared objects under UNIX).</ol>
<br>
2.	You must decide on a mnemonic class name for the database format that your driver will access. The class name can be up to five characters long. Preferably, it is nationality-neutral (obscure in all languages); for example, DBASE. You supply the class name as the first parameter when you call @DbLookup and @DbColumn.<br>
<br>
3.	The file name for a database driver must be in the following format:  a platform-dependent prefix, followed by the class name, followed by a platform-dependent file extension (if required). The prefixes and extensions required for each platform are as follows:
<ul><br>
Windows 32-bit:	prefix:  &quot;ndb&quot;	file extension:  &quot;.dll&quot;<br>
AIX:	prefix:  &quot;libdb&quot;	file extension:  &quot;.a&quot;<br>
Linux:	prefix   &quot;libdb&quot;             file extension: &quot;.so&quot;<br>
<br>
Therefore, for a database with the class name &quot;abc&quot;, the filenames for the database driver on the various platforms would be:<br>
<br>
Windows 32-bit:	&quot;ndbabc.dll&quot;<br>
AIX: 	&quot;libdbabc.a&quot;<br>
Linux:                                     &quot;libdbabc.so&quot;<br>
<br>
To install the database driver, place its executable program library into the Domino or Notes program directory.</ul>
<br>
4.	Under Windows, the module definition file (.DEF file) must specify the data as being MOVEABLE SINGLE so that it doesn't occupy GlobalDOS memory and because Windows doesn't support multi-instance dynamic link libraries. <br>
<br>
5.	Because of instantiation requirements of the operating systems, the library is loaded once per process. At load time under Windows, the first entry point address (entry point @1) is obtained by ordinal and the driver's Init function is invoked. Under UNIX, use MainEntryPoint for the driver's Init function.   The principal use of this function is to plug a data structure with vectors to other database driver subroutines, including its Term function, which will be called by Domino or Notes when the process exits or calls<b><font color="#FF0000"> </font></b>NotesTerm.<br>

<ul>Remember that in some environments (such as Windows), you must export in your DEF file all of your functions that Domino or Notes will call through these vectors. This is because these environments use the fact that it<b><font color="#FF0000"> </font></b>is exported to generate a thunk that sets up the program's DS appropriately on all of these entry points. Under AIX, you must create an export file and define the exported symbols.  <font color="#FF0000"> </font></ul>
<br>
6.	As in all Domino and Notes subsystems, all entry points to the drivers must be<b><font color="#FF0000"> </font></b>completely reentrant, both by multiple threads in a single process and by multiple processes. In Windows, reentrancy is also a requirement, since if you call Yield, you may also be preempted by another process that does a database driver call. (Domino and Note makes heavy use of multiple threads and multiple processes, so treat this as a requirement, not as something that can be done &quot;later&quot;.)<br>
<br>
7.	As you will note later, the database driver is responsible for maintaining queues (or arrays) of data structures internally. Therefore, be aware that shared memory in UNIX does not exist at the same place in address spaces of multiple processes, so you cannot have address-based queues in shared memory. If you use MULTIPLE on your executable program libraries and keep such queues in the<b><font color="#FF0000"> </font></b>local heap, or use non-shared memory for your queues, you should be safe.<br>
<br>
<b><font size="5" color="#000080">Database Driver Header Files and Error Status Codes</font></b><br>
<br>
The database driver needs to include two C API header files. dbdrv.h contains the definition of the database driver vector structure filled in by the initialization routine and  miscellaneous constants. dbdrverr.h contains error status code definitions that span all drivers. If a database driver must return error codes not contained in dbdrverr.h, the codes should be in the range 0x31B4 (PKG_DBD+180)  through 0x31B7 (PKG_DBD+183) inclusive, so that they don't overlap other Domino and Notes error codes.<br>
<br>
<br>
<b><font size="5" color="#000080">Database Driver Initialization and Termination</font></b>
<ul></ul>
The driver's library is loaded once per process. At load time under Windows, the first entry point address (entry point @1) is obtained by ordinal and the driver's Init function is invoked. Under UNIX, the entry point, which is<b><font color="#FF0000"> </font></b>the driver's Init function, must be called MainEntryPoint.<br>
<br>
The principal use of the driver's Init function is to return a vector of other driver subroutine addresses, defined in the DBVEC data structure in the header file dbdrv.h. Your driver should not define a function for the SetOpenContext member of the DBVEC data structure. This function is reserved for use by Domino and Notes.<br>
<br>
Because the database driver's Init function is passed a context block containing the driver's module handle, you can also use it to load strings or other resources from the driver's module.<br>
<br>
NotesTerm invokes the driver's Term function just prior to this process's exit. The higher layers of software guarantee that it will already have asked the driver to close all open databases/sessions prior to calling Term, so the Term routine probably needs to do nothing.<br>
<br>
You can use the following code as a template for the Init and Term functions for a database driver. <br>
<br>
NOTE: The format of the session queue is defined by the database driver, not by Domino or Notes. This code shows one way to initialize a session queue.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>Database Initialization and Termination; MainEntryPoint(), DBDTerm() templates.</b></ul>
</td></tr>
</table>
<br>
<tt><font size="2">/* &nbsp;Initialize the database driver<br>
 *<br>
 * &nbsp;Do per-process initialization. This is called just after<br>
 * &nbsp;the LoadLibrary and is the first entry point in the library.<br>
 * &nbsp;When this entry point is called, all the other entry point<br>
 * &nbsp;vectors are filled in by this routine.<br>
 *<br>
 * &nbsp;Inputs:<br>
 * &nbsp; &nbsp; &nbsp;drv - database driver vector<br>
 *<br>
 * &nbsp;Outputs:<br>
 * &nbsp; &nbsp; &nbsp;(routine) - error status<br>
 * &nbsp; &nbsp; &nbsp;drv vectors to other subroutines have been filled in<br>
 *<br>
 */</font></tt><br>
<br>
<tt><font size="2">STATUS LNPUBLIC MainEntryPoint(DBVEC *drv)</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; {</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Fill in the subroutine vectors */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; drv-&gt;Init = MainEntryPoint;<br>
 &nbsp; &nbsp;drv-&gt;Term = DBDTerm;<br>
 &nbsp; &nbsp;drv-&gt;Open = DBDOpen;<br>
 &nbsp; &nbsp;drv-&gt;Close = DBDClose;<br>
 &nbsp; &nbsp;drv-&gt;Function = DBDPerformFunction;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Perform one-time initializations by initializing local</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;* &nbsp;session queue if it hasn't yet been initialized. (In</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;* &nbsp;Windows, with single-instance DS, this is a queue shared</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;* &nbsp;by all processes. In all other environments, it's</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;* &nbsp;process-private. </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (SessionQueue.Next == NULL)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;SessionQueue.Next = SessionQueue.Prev = &amp;SessionQueue;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Done */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return(NOERROR);<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<br>
<tt><font size="2">/* &nbsp;Terminate the database driver<br>
 *<br>
 * &nbsp;Per-process termination routine, ASSUMING that all open <br>
 * &nbsp;sessions for this context have been closed by the time <br>
 * &nbsp;this is called. &nbsp;This is called just prior to the </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp;</font></tt><tt><font size="2">FreeLibrary.<br>
 *<br>
 * &nbsp;Inputs:<br>
 * &nbsp; &nbsp; &nbsp;drv - database driver vector<br>
 *<br>
 * &nbsp;Outputs:<br>
 * &nbsp; &nbsp; &nbsp;(routine) - error status<br>
 *<br>
 */</font></tt><br>
<br>
<tt><font size="2">STATUS LNPUBLIC DBDTerm(DBVEC *drv)</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; {</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Your per-process termination code here */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return(NOERROR);<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">Database Driver Sessions</font></b><br>
<br>
Because of the semantics of the @Db functions, Domino and Notes request the database driver to perform @DbLookup and @DbColumn functions without any &quot;handle&quot; to an open database table. Furthermore, it expects that the operation will be extremely fast, so it doesn't want the driver to open and close the database on every Function request. For this reason Domino and Notes, in cooperation with the drivers, implements the abstraction of a &quot;session.&quot;<br>
<br>
Before issuing a function request from a thread, Domino or Notes ask the database driver to open a session. At this point, the driver merely allocates a small data structure and returns an opaque handle to its caller, which Domino or Notes will then pass to the driver on future function requests. Every time the driver has to open a database in response to a function request, the open database context is maintained by enqueueing it off the session data structure. Future function requests on that session use the same, already-open database context.<br>
<br>
It is important to understand the usage and scope of a session. First, Domino or Notes guarantees that a session, once opened, will only be used by the thread that requested the open. That is, Domino and Notes do not pass session handles between processes or threads. Second, a single thread may have multiple sessions open at any given time. Third, functions will be performed on the same database in multiple sessions, perhaps by the same thread and perhaps by a different thread. Last, sessions stay open for a long time. They open when a user double-clicks on a database icon and close when a user closes<b><font color="#FF0000"> </font></b>the database, which could be much later.<br>
<br>
NOTE:	Since the maintenance of session queues and database contexts is the responsibility of the database driver, their design is up to the designer of the driver. For some applications, dynamically-allocated linked lists might be the best solution; for others, a statically-defined array might be more appropriate.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>Open and Close a Session; DBDOpen, DBDClose Templates</b></ul>
</td></tr>
</table>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp;/* &nbsp;Open a session<br>
 *<br>
 * &nbsp;Any databases opened as a side effect of Functions<br>
 * &nbsp;performed on this session will gather up their context <br>
 * &nbsp;in the hSession returned by this routine.<br>
 *<br>
 * &nbsp;Inputs:<br>
 * &nbsp; &nbsp; &nbsp;drv - database driver vector<br>
 *<br>
 * &nbsp;Outputs:<br>
 * &nbsp; &nbsp; &nbsp;*rethSession = filled in with session handle<br>
 * &nbsp; &nbsp; &nbsp;(routine) - error status<br>
 *<br>
 */</font></tt><br>
<br>
<br>
<tt><font size="2">STATUS LNPUBLIC DBDOpen(DBVEC *drv, HDBDSESSION *rethSession)</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; {<br>
 &nbsp; &nbsp;STATUS error;<br>
 &nbsp; &nbsp;SESSION *sess;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Allocate a new, empty session context block and enqueue it. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = Alloc(sizeof(SESSION), &amp;sess))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return(error);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; sess-&gt;DatabaseQueue.Next = sess-&gt;DatabaseQueue.Prev =</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;sess-&gt;DatabaseQueueQueue;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; Enqueue(&amp;SessionQueue, sess);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Return it to the caller as an opaque handle. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; *rethSession = (HDBDSESSION) sess;<br>
 &nbsp; &nbsp;return(NOERROR);<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">/* &nbsp;Close an open session<br>
 *<br>
 * &nbsp;Close a session, and as a side effect all databases whose context<br>
 * &nbsp;has been built up in hSession.<br>
 *<br>
 * &nbsp;Inputs:<br>
 * &nbsp; &nbsp; &nbsp;drv - database driver vector<br>
 * &nbsp; &nbsp; &nbsp;hSession - session handle to close<br>
 *<br>
 * &nbsp;Outputs:<br>
 * &nbsp; &nbsp; &nbsp;(routine) - error status<br>
 *<br>
 */</font></tt><br>
<tt><font size="2">&nbsp;</font></tt><br>
<tt><font size="2">STATUS LNPUBLIC DBDClose(DBVEC *drv, HDBDSESSION hSession)</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;{<br>
 &nbsp; &nbsp;SESSION *sess = (SESSION *) hSession;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Close and deallocate all open database/table descriptors */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; while (!QueueIsEmpty(&amp;sess-&gt;DatabaseQueue))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;DATABASE *db = (DATABASE *) &amp;sess-&gt;DatabaseQueue.Next;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;CloseDatabaseTable(sess, db);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;Dequeue(db);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;Free(db);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Dequeue and deallocate the session itself. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; Dequeue(sess);<br>
 &nbsp; &nbsp;Free(sess);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Done */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return(NOERROR);<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">Database Driver Functions</font></b><br>
<br>
A single entry point to the driver performs all database functions. Currently, the only supported database functions are @DbLookup and @DbColumn. The function entry point is a generalized argc/argv interface, except that the arguments are Domino data types, not C char *'s, and there is an &quot;argl&quot; vector containing the lengths of the objects at which the argv's point. If the function executes without error, it must allocate a Domino memory object (OSMemAlloc) containing the resulting Domino data. Correlation between the input argument data types and the output data type is not necessary.<br>
<br>
Remember that the first WORD of Domino data is a standard Domino data type, followed by the actual data. (For more information, see the Reference.) Anticipate and handle the following data types by converting them as necessary to the type you need for your query. If you receive any other data type, you can fail the query and return the error ERR_DBD_DATATYPE. As always in Domino and Notes, all text is in LMBCS.<br>
<br>
<tt>&nbsp; &nbsp; TYPE_TEXT<br>
 &nbsp; &nbsp;TYPE_TEXT_LIST<br>
 &nbsp; &nbsp;TYPE_NUMBER<br>
 &nbsp; &nbsp;TYPE_NUMBER_RANGE<br>
 &nbsp; &nbsp;TYPE_TIME<br>
 &nbsp; &nbsp;TYPE_TIME_RANGE</tt><br>
<br>
The actual format of the content of<b><font color="#FF0000"> </font></b>the arguments is up to the database driver,  although the sample code below follows the convention of using the first available argument (the database driver name having already been stripped off) as the database file name and the second argument as the table name. For instance, if the design of the database accessed by your driver does not include the notion of a table, you can us the second argument to specify some other information that applies to your database. Of course, you must document this change for users of your database driver.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>Perform a Database Driver Function; DBDPerformFunction Template.</b></ul>
</td></tr>
</table>
<br>
<tt><font size="2">/* &nbsp;Perform a database function<br>
 *<br>
 * &nbsp;Perform a function on a session. &nbsp;If any databases must be opened<br>
 * &nbsp;as a side effect of this function, gather context into hSession<br>
 * &nbsp;so that it may be later deallocated/closed in Close.<br>
 *<br>
 * &nbsp;Inputs:<br>
 * &nbsp; &nbsp; &nbsp;drv - database driver vector<br>
 * &nbsp; &nbsp; &nbsp;Function - function ID<br>
 * &nbsp; &nbsp; &nbsp;argc - number of arguments<br>
 * &nbsp; &nbsp; &nbsp;argl - array of argument lengths<br>
 * &nbsp; &nbsp; &nbsp;argv - array of argument pointers<br>
 *<br>
 * &nbsp;Outputs:<br>
 * &nbsp; &nbsp; &nbsp;*rethResult = filled in with result handle<br>
 * &nbsp; &nbsp; &nbsp;*retResultLength = filled in with result buffer length<br>
 * &nbsp; &nbsp; &nbsp;(routine) - error status<br>
 *<br>
 */</font></tt><br>
<br>
<tt><font size="2">STATUS LNPUBLIC DBDPerformFunction(DBVEC *drv, HDBDSESSION hSession,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;WORD Function,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;WORD argc, DWORD *argl, void **argv,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;HANDLE *rethResult, DWORD *retResultLength)</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; {<br>
 &nbsp; &nbsp;SESSION *sess = (SESSION *) hSession;<br>
 &nbsp; &nbsp;DATABASE *db;<br>
 &nbsp; &nbsp;STATUS error;<br>
 &nbsp; &nbsp;char *DbName;<br>
 &nbsp; &nbsp;WORD DbNameLength,<br>
 &nbsp; &nbsp;char *TableName;<br>
 &nbsp; &nbsp;WORD TableNameLength,</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Check args and extract database/table name */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (argc &lt; 2)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return(ERR_DBD_INSUFF_ARGS);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; DbName = argv[0];<br>
 &nbsp; &nbsp;DbNameLength = (WORD) argl[0];<br>
 &nbsp; &nbsp;TableName = argv[1];<br>
 &nbsp; &nbsp;TableNameLength = (WORD) argl[1]);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; argc -= 2;<br>
 &nbsp; &nbsp;argv += 2;<br>
 &nbsp; &nbsp;argl += 2;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Find an instance of the open database on this session. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; for (db = (DATABASE *) &amp;sess-&gt;DatabaseQueue.Next;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;!IsQueueHead(&amp;sess-&gt;DatabaseQueue, db);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;db = (DATABASE *) db-&gt;Links.Next))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (DbNameLength != db-&gt;DbNameLength)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;continue;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (TableNameLength != db-&gt;TableNameLength)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;continue;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (memcmp(DbName, db-&gt;DbName, DbNameLength) != 0)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;continue;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (memcmp(TableName, db-&gt;TableName, TableNameLength) != 0)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;continue;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;break;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;If not found on queue, open and enqueue it. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (IsQueueHead(&amp;sess-&gt;DatabaseQueue, db))<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (error = Alloc(sizeof(DATABASE), &amp;db))<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return(error);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; db-&gt;DbName = DbName;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;db-&gt;DbNameLength = DbNameLength;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;db-&gt;TableName = TableName;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;db-&gt;TableNameLength = TableNameLength;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (error = OpenDatabaseTable(sess, db))<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Free(db);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return(error);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; Enqueue(&amp;sess-&gt;DatabaseQueue, db);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; }</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Dispatch based upon function */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; switch (Function)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /* &nbsp;Process LOOKUP */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; case DB_LOOKUP:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error = Lookup(db, argc, argl, argv, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;rethResult, retResultLength);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /* &nbsp;Process COLUMN */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; case DB_COLUMN:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error = Column(db, argc, argl, argv, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;rethResult, retResultLength);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /* &nbsp;Unknown function */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; default:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error = ERR_DBD_FUNCTION;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; }</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Done */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return(error);<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">Query/Result Caching</font></b><br>
<br>
The higher layers of software in Domino and Notes outside of the database driver cache complete queries and their results for moderate periods. You can override this caching by using a special &quot;nocache&quot; qualifier, but this is usually unnecessary and unused. As long as the database driver's implementation of @DbLookup and @DBColumn has no side effects (and it shouldn't, given the semantics), caching should work well across driver implementations.
---
