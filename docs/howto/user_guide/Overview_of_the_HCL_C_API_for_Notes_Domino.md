##### Chapter 1-1
##### Overview of the HCL C API for Notes/Domino

<b><font size="5" color="#000080">What is the HCL C API for Notes/Domino?</font></b><br>
<br>
The HCL C API for Notes/Domino is a set of subroutines and data structures that allows you to write programs that access Domino databases. The C API subroutines are written in C and you call them from C programs. <br>
<br>
With the HCL C API for Notes/Domino, you can write programs that perform a significant subset of the operations available through the Notes user interface and some operations that are not available through the user interface.<br>
<br>
<br>
<b><font size="5" color="#000080">Operating Environments</font></b><br>
<br>
The HCL C API for Notes/Domino supports the same operating environments supported by Notes and Domino.<br>
<br>
Likewise, development of IBM i applications requires the HCL C API Toolkit for Notes/Domino for IBM i.<br>
<br>
Except where noted in the <i>Reference ,</i> you can use each C API function under all operating environments.<br>
<br>
<br>
<b><font size="5" color="#000080">Capabilities of the HCL C API for Notes/Domino</font></b><br>
<br>
Before using the HCL C API for Notes/Domino, it is important to understand what it is designed to do. The C API is a powerful tool, but like any tool it has a few restrictions.<br>
<br>
<br>
<b><font size="4" color="#000080">What the HCL C API for Notes/Domino Can Do</font></b><br>
<br>
The HCL C API for Notes/Domino gives you access to many features of the Notes user interface and a few features that are not found in the user interface. For example, you can:<br>

<ul type="disc">
<li>Create new Domino databases and delete unneeded databases.
<li>Read, write, and modify any document in a database.
<li>Read, write, and modify any of the fields in a document.
<li>Create and use database indexes (views).
<li>Control database access, both with user access lists and roles.
<li>Query and manipulate busy times in the free time database (busytime.nsf).
<li>Gather and report HCL Domino Server performance statistics.
<li>Write custom tasks and add them to the HCL Domino server software.
<ul></ul>
</ul>
The C API allows you to treat databases at a high level by creating and deleting entire databases. You can also copy database elements (macros, forms, views, icons, and so on) intact between databases. <br>
<br>
You can use the C API to perform any operation on documents and fields in documents. You can create new documents, delete existing documents, and copy documents from one database to another. You can add fields to documents, delete fields from documents, copy fields between documents, read fields, and write into fields.<br>
<br>
The C API gives you powerful access to Domino database design features. You can create new views, build indexes using these views, and read the list of documents in a view. You can create new forms and lay out the forms any way you want. You can create or modify agents and run them from a C API program or from Domino or Notes.<br>
<br>
The C API also gives you access to some of the Domino system administration features. You can set the user access list on a database, control database privileges, examine the performance statistics gathered by a server, generate server &quot;software events,&quot; and consume events that you have generated.<br>
<br>
You can query and manipulate busy-time information in the free time database (busytime.nsf) by using the Scheduling APIs.<br>
<br>
Finally, the C API lets you extend the software with user-written &quot;add-ins.&quot; An add-in can be on the Notes workstation and present the user with your own pull-down menu choices, or it can be on the HCL Domino server, where it forms a new server task that runs alongside the standard HCL Domino server tasks.<br>
<br>
<br>
<b><font size="4" color="#000080">What the HCL C API for Notes/Domino Cannot Do</font></b><br>
<br>
The C API does not let you modify the existing software. You cannot use the C API to remove features that Domino or Notes already has or to change the way a Domino or Notes feature works. For example, you cannot use the C API to modify how the Notes editor operates or to remove the Help pull-down menus.<br>
<br>
You cannot use the C API to directly change database user activity logs, or database icons.<br>
<br>
You cannot use the C API to access Workstation Security options or the user's Execution Control List (ECL).<br>
<br>
You cannot use the C API to manipulate the shared mail database.<br>
 <br>
<br>
<b><font size="4" color="#000080">Summary</font></b><br>
<br>
The chart below summarizes the capabilities of the HCL C API for Notes/Domino.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="39%"><img width="1" height="1" src="../images/Overview_of_the_HCL_C_API_for_Notes_Domino0.gif" border="0" alt=""></td><td width="20%"><b>Read</b></td><td width="20%"><b>Write</b></td><td width="20%"><b>Use</b></td></tr>

<tr valign="top"><td width="39%"><b>DB Title</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">n/a</td></tr>

<tr valign="top"><td width="39%"><b>DB Access Control</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">automatic</td></tr>

<tr valign="top"><td width="39%"><b>DB Replication Settings</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">n/a</td></tr>

<tr valign="top"><td width="39%"><b>DB Replication History</b></td><td width="20%">YES</td><td width="20%">YES (Clear the replication history only)</td><td width="20%">n/a</td></tr>

<tr valign="top"><td width="39%"><b>DB Activity Log</b></td><td width="20%">YES</td><td width="20%">NO</td><td width="20%">n/a</td></tr>

<tr valign="top"><td width="39%"><b>DB Policy Document</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">n/a</td></tr>

<tr valign="top"><td width="39%"><b>DB Help Document</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">n/a</td></tr>

<tr valign="top"><td width="39%"><b>Document</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">n/a</td></tr>

<tr valign="top"><td width="39%"><b>Form</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">n/a</td></tr>

<tr valign="top"><td width="39%"><b>View</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">YES</td></tr>

<tr valign="top"><td width="39%"><b>Macro</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">YES</td></tr>

<tr valign="top"><td width="39%"><b>Icon</b></td><td width="20%">NO</td><td width="20%">NO</td><td width="20%">n/a</td></tr>

<tr valign="top"><td width="39%"><b>Formula</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">YES</td></tr>

<tr valign="top"><td width="39%"><b>Field (all data types)</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">n/a</td></tr>

<tr valign="top"><td width="39%"><b>Encrypted Field</b></td><td width="20%">YES</td><td width="20%">YES</td><td width="20%">n/a</td></tr>
</table>
<br>
<br>
<b><font size="5" color="#000080">Applying the HCL C API for Notes/Domino</font></b><br>
<br>
You can use the C API to create a wide variety of applications.<br>
<br>
One common use of the C API is to create file import/export programs for Notes. A file export program might read a database, extract some of the documents, and put them into a format compatible with a certain typesetter. You might also write a file import program that reads a non-Domino MIS database and creates documents based on the information in the MIS database.<br>
<br>
Another application for the C API is periodic maintenance of databases. For example, you can write a program that scans a phone-message database and deletes every message that is more than six months old.<br>
<br>
Still another use for the C API is to create databases that combine data from existing databases. You might write a program that reads the databases maintained by each department in your company and then creates a new database containing company-wide information culled from the departments.<br>
<br>
You can also use the C API to design databases based on criteria available to the program at run time. For example, a program can receive a mail message with a set of data and a list of user names. The C API can create a new database, design a form and view for displaying the data, and add the user names to the access list for the database.<br>
<br>
Any program using the C API can work with other software products using the other software product's API. For example, a program might use an API to read data from a relational database, and then use the C API to write that data to a Domino database.
<p><br>
<b><font size="5" color="#000080">Formats for HCL C API Programs for Notes/Domino</font></b><br>
<br>
Programs written using the C API may take a variety of formats. Specifically, you can package C API code into:<br>

<ul type="disc">
<li>Stand-alone applications
<li>HCL Domino server add-in tasks
<li>Notes workstation menu add-ins
<li>Notes workstation import and export libraries
<li>Database hook drivers
<li>Extension manager hook libraries
<li>Drivers for external (non-Domino) databases
<ul></ul>
</ul>
In all of these program formats, the &quot;core&quot; C API code is essentially the same: you use the same C API routines to operate on a database. However, depending on the format, there are variations in the entry and exit code and the program start-up method.<br>
<br>
<br>
<b><font size="4" color="#000080">Stand-Alone Applications</font></b><br>
<br>
Stand-alone C API applications are main programs that make C API calls into the Domino or Notes software.  Domino server or Notes workstation software does not need to be running before you run these programs.
<ul>
<ul></ul>
</ul>
<br>
<b><font size="4" color="#000080">HCL Domino Server Add-In Tasks</font></b><br>
<br>
HCL Domino server add-in tasks are custom tasks that you write and add to the set of tasks in the HCL Domino server software. <br>
<br>
The HCL Domino server software is composed of approximately eight standard tasks that carry out the server's functions. An add-in task is added to this set and can include any of the C API operations described above. In addition, you can specify the schedule under which the custom task executes. For example, you can run a job each night at 2:00 A.M., every hour, or once per week.<br>
<br>
<br>
<b><font size="4" color="#000080">Notes Workstation Menu Add-Ins</font></b><br>
<br>
Notes workstation add-ins are custom libraries that you write and add to the Notes pull-down menu structure. <br>
<br>
A workstation menu add-in can include any of the C API operations. The add-in can create new options in the Notes pull-down menu structure and receive control when the user selects one of these choices. Workstation menu add-ins also have the ability to place text at the cursor location when the user is composing a document.<br>
<br>
Currently, you can create<font color="#FF0000"> </font>workstation menu add-ins with the Windows version of Notes, where they are built as dynamic link libraries (DLLs).<br>
<br>
<br>
<b><font size="4" color="#000080">Notes Workstation Import and Export Libraries</font></b><br>
<br>
Notes workstation import/export libraries are custom libraries that you write and add to the set of Notes import or export choices.<br>
<br>
The list of import and export choices available through the Notes user interface is controlled by a matching set of libraries. You can create your own import or export library containing the C API code that imports or exports a new type of file or text. After creating the library, you add it to the set of import/export libraries that is supplied with Notes. The new option appears in the Notes user interface in the import or export dialog box.<br>
<br>
Currently, you can add import/export libraries to Notes workstations that run under Windows. You build these libraries as DLLs. <br>
<br>
<br>
<b><font size="4" color="#000080">Database Hook Drivers</font></b><br>
<br>
Database hook drivers are programs that gain control each time a document is opened, updated, or categorized.<br>
<br>
<br>
<b><font size="4" color="#000080">Extension manager hook libraries</font></b><br>
<br>
The Extension Manager loads a shared executable library (for example, a Windows DLL) which can then specify a callback routine to be called before or after Domino or Notes performs internal processing. You can use this feature to track the internal activity of Domino or Notes, perform processing in addition to the standard Domino or Notes processing, or extend the operation of Domino or Notes.<br>
<br>
<br>
<b><font size="4" color="#000080">Drivers for External (Non-Domino) Databases</font></b><br>
<br>
External database drivers are custom libraries you write that let you use the @DbLookup and @DbColumn functions to access<font color="#FF0000"> </font>data in your own non-Domino databases. <br>
<br>
<br>
<b><font size="5" color="#000080">Initializing C API Structures</font></b><br>
<br>
The C API Toolkit contains definitions for many data structures that are passed into Domino and Notes.  When setting C API data structures, first initialize the values of structure members to 0.  This will ensure optional structure members are initialized properly.<br>
<br>
<br>
<b><font size="5" color="#000080">Return Values of Type STATUS</font></b><br>
<br>
Many C API functions return a value of type STATUS. A special STATUS value, NOERROR, is defined as zero in the C API. Therefore, C API programs can detect error conditions by checking to see if the STATUS value is logically TRUE. If such a C API function returns a STATUS value other than NOERROR, any output parameter passed into the function may be returned with an undefined value. Do not try to access these output parameters when a C API function returns a STATUS other than NOERROR.<br>
<br>
The 16-bit value of a STATUS error code consists of the following fields:
<ul>
<ul>1 bit:	Flag bit - status message has been displayed.<br>
1 bit:	Flag bit - status message came from a remote machine (i.e., a server).<br>
6 bits:	Package code or partial package code.<br>
8 bits:	Status value or partial package code plus status value.<br>
</ul>
</ul>
STATUS values are associated with error strings.  Error strings are categorized by package (subsystem) code.  Package codes are defined in globerr.h.  The error strings are defined in the corresponding package's err.h file.  For example, suppose you get a return STATUS code of 18867 in decimal:<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="11%"><div align="center"><b>Decimal</b></div></td><td width="10%"><div align="center"><b>Hex</b></div></td><td width="18%"><div align="center"><b>Binary</b></div></td><td width="12%"><div align="center"><b>Flag Bit</b></div></td><td width="15%"><div align="center"><b>Package Code plus Status Value</b><br>
<b>(hex)</b></div></td><td width="15%"><div align="center"><b>Status Value </b><br>
<b>(hex)</b></div></td><td width="19%"><div align="center"><b>Status Value </b><br>
<b>(decimal)</b></div></td></tr>

<tr valign="top"><td width="11%"><div align="center">18867</div></td><td width="10%"><div align="center">49B3</div></td><td width="18%"><div align="center"><b><font color="#000080">01</font></b>00  1001  1011  0011</div></td><td width="12%"><div align="center"><b><font color="#000080">01</font></b></div></td><td width="15%"><div align="center">09B3</div></td><td width="15%"><div align="center">B3</div></td><td width="19%"><div align="center">179</div></td></tr>
</table>
<div align="center"></div>The first two bits in this example, 01,  indicate that the status message came from a remote machine.  Clearing this bit leaves us with the package code plus the status value, 09B3, which are used to identify the error string.  The package codes are defined in the C API header file,  globerr.h.  Look for the closest package code that is less than or equal to 09B3.  <br>

<ul>#define PKG_ASSISTANT 0x0880 /* Your codes are limited to 0 - 127 */<br>
<b><font color="#000080">#define PKG_SERVER 0x0900</font></b><br>
#define PKG_NETWORK 0x0A00</ul>
<br>
In our example, the package code is 0x0900 which is PKG_SERVER.  That leaves B3 as the status value which equals 179 decimal.  The error strings for the PKG_SERVER package are in srverr.h.<br>

<ul><b><font color="#000080">#define ERR_SERVER_NO_RESPONSE PKG_SERVER+179</font></b><br>
<b><font color="#000080">	errortext(ERR_SERVER_NO_RESPONSE,&quot;No response from server for this command&quot;)</font></b></ul>
<br>
The C API function OSLoadString translates a C API error code of type STATUS into a character string. <br>
<br>
<br>
<b><font size="5" color="#000080">Debug Options</font></b><br>
<br>
<b><font size="4" color="#000080">&quot;Just In Time&quot; (JIT) Debugger</font></b><br>
<br>
<u>Windows only:</u>  Beginning with the Notes/Domino 6 release, the method by which Notes/Domino software functions following a crash has been modified.  <br>
<br>
In the past Notes/Domino would, in the event of a crash, invoke the system's &quot;Just In Time&quot; (JIT) debugger (e.g. Dr. Watson, QNC, MSDEV), but with Notes/Domino 6 this is no longer the case.  To aid C API developers, the notes.ini variable, APIDevloper = 1, has been implemented.  <br>
<br>
When the APIDeveloper = 1 variable is added to the notes.ini file, C API developers can again capture and debug a crashing application using the JIT, much like they could in pre Notes/Domino 6 releases.<br>
<br>
In the event of a crash, all Notes/Domino related processes must be terminated before any of them can be restarted.<br>

---
