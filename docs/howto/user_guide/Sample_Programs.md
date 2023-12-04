##### Chapter 2-3
##### Sample Programs

<b><font size="5" color="#000080">Overview</font></b><br>
<br>
The HCL C API Toolkit<font color="#FF0000"> </font>for Domino and Notes contains many sample programs that show you how to use various aspects of the C API. The samples are divided into the following groups:<br>

<ul>
<ul><b>Administration</b><br>
Programs that show how to perform Domino system administration operations like controlling database access and checking server performance<br>
<br>
<b>Advanced Server</b><br>
Programs that illustrate how to use the C API to develop applications that manage clustered servers and databases and implement customized billing managers and add-in tasks<br>
<br>
<b>Basic</b><br>
Programs that show the basic structure of API code or basic operations using the C API<br>
<br>
<b>Client</b><br>
Programs that show the structure of client specific API code or operations using the C API<br>
<br>
<b>Database Design</b><br>
Programs that show how to create and read database design elements, including forms, views, navigators, agents, access control lists, and policy and help documents<br>
<br>
<b>DB2</b><br>
Programs that show the structure of DB2 specific API code<br>
<br>
<b>Mail</b><br>
Programs that show how to use the C API for electronic mail operations, such as sending and receiving mail and writing mail gateways<br>
<br>
<b>Miscellaneous</b><br>
Programs that show various C API operations not covered by the other samples<br>
<br>
<b>Rich Text</b><br>
Programs that show how to read and write elements of a rich text field<br>
<br>
<b>Server</b><br>
Programs that show the structure of HCL Domino Server add-in tasks and features of the HCL Domino Server environment<br>
<br>
<b>Views</b><br>
Programs that show how to use indexes (views)<br>
<br>
<b>HTML</b><br>
Programs that show how to use HTML functions<br>
<br>
<b>CALAPI</b><br>
Programs that show how to use iCalendar functions<br>
<br>
<b>OS</b><br>
Programs that show how to use  C API for OS operations.<br>
<br>
<b>TIME</b><br>
Program that shows how to use time conversion operations.<br>
</ul>
</ul>
The sample descriptions below indicate the platforms each sample supports. Some samples do not support all platforms, but each sample contains valuable code relevant to all platforms. HCL C API functions for Domino and Notes are largely the same on every platform. Frequently, only the makefile varies from platform to platform.<br>
<br>
Note that the sample programs use the minimum stack sizes necessary for execution. Other applications may require larger stack sizes. <br>
		<br>
<br>
<b><font size="5" color="#000080">Basic</font></b><br>
<br>
These programs are in the <i>basic</i> samples directory.<br>
<br>
ALLFLDS <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i><br>
Finds all the fields in all the documents in a database<br>
<br>
CAPIERR (<i>Windows</i>)<br>
Shows how to load an error message string given a Domino or Notes error code, from a Windows MFC C++ application.<br>
<br>
COPYDB <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i> <br>
Copies all the components of one database to another<br>
<br>
CPNOTES <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i><br>
Selectively copies documents from one database to another based on various criteria, including modification time<br>
<br>
DBPROPS (<i>Windows</i>, IBM i, <i>Linux</i>)<br>
Shows  how to get and set some of the database properties available to the HCL C API.<br>
<br>
GETBUILD <i>(</i><i>Windows,  AIX, Linux RedHat, IBM i)</i> <br>
Shows how to get the major build number identifying the version of Domino or Notes installed<br>
<br>
INTRO <i>(</i><i>Windows,  AIX, Linux RedHat, IBM i)</i> <br>
Shows the basic structure of a character-mode HCL C API program, as well as how to access a database that is on a remote HCL Domino Server.  Uses main as the main entry point.<br>
<br>
INTROWIN <i>(</i><i>Windows)</i><br>
Shows the basic structure of a Windows application that makes HCL C API calls<br>
<br>
MSIMPLE <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i> <br>
Modifies fields with simple data types<br>
<br>
NOTESMAIN  <i>(Windows,  AIX, IBM i, Linux RedHat, )</i><br>
Shows the basic structure of a character-mode HCL C API program, as well as how to access a database that is on a remote HCL Domino Server.  Uses NotesMain as the main entry point. <br>
<br>
NUMLIST <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i><br>
Writes a field of type number list<br>
<br>
RSIMPLE <i>(Windows, AIX, Linux RedHat, IBM i)</i><br>
Reads fields with simple data types <br>
(This sample demonstrates a basic sequential search of a database.)<br>
   <br>
SRCH_ALL <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i><br>
Search for and process all documents in a database<br>
(This sample shows how to guarantee that each document is only processed once during a sequential search.)<br>
<br>
SUMMARY <i>(</i><i>Windows, AIX,  Linux RedHat, IBM i)</i><br>
Finds and prints all summary data of all data notes in a database, without opening the data notes<br>
<br>
WSIMPLE <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i><br>
Writes fields with simple data types: text, number, date/time, text list<br>
<br>
sizeofHANDLE <i>(Windows, IBM i)</i><br>
Show length of some HANDLEs<br>
<br>
<b><font size="5" color="#000080">Views</font></b><br>
<br>
These programs are in the <i>views</i> samples directory.<br>
<br>
NAMELOOK <i>(</i><i>Windows, IBM i, Linux)</i><br>
Look up names in the Personal  Address book and retrieve items<br>
<br>
NAVIGATE <i>(</i><i>Windows, IBM i, Linux)</i><br>
Performs complex navigation of a view index<br>
<br>
ONECAT <i>(</i><i>Windows, IBM i, Linux)</i><br>
Lists all the documents in one category in a view<br>
<br>
TEXTKEY <i>(</i><i>Windows, IBM i, Linux)</i><br>
Finds documents in a view based on a single text key<br>
<br>
TWOKEY (<i>Windows, AIX, IBM i, Linux RedHat</i>) <br>
Finds documents in a view based on two sort keys of different data types<br>
<br>
VIEWIDS <i>(Windows, AIX,Linux RedHat, IBM i)</i><br>
Finds all the documents in a view and lists their note IDs<br>
<br>
VIEWSUMM <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i><br>
Prints the summary information in a view <br>
(This program essentially duplicates a view as you see it at the user interface. The view summary is useful because it allows you to extract fields from the documents in a view without opening the documents.)<br>
<br>
<br>
<b><font size="5" color="#000080">Rich Text</font></b><br>
<br>
These programs are in the <i>richtext</i> samples directory.<br>
<br>
BIG_RICH <i>(</i><i>Windows, Linux) </i><br>
Creates rich text fields from character text files up to five megabytes long using Compound Text functions<br>
<br>
CDFILE <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i><br>
Two programs to read and write a rich text (CD) file: CDFWRITE writes text to a CD file, and CDFREAD reads a CD file and stores it in the rich text field of a document<br>
<br>
DOCLINK <i>(</i><i>Windows, IBM i)</i><br>
Adds a document link, a view link and a database link to a rich text field, using the low-level structures of a document, view and database link<br>
<br>
DUMPFONT <i>(Windows, AIX, Linux RedHat, IBM i)</i><br>
Locates and prints out the font tables in all data notes<br>
<br>
DYNAMIC <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i><br>
Same as WRICH, but uses dynamic allocation of the data structures<br>
(This technique is useful if you do not know at compile time exactly what the rich<font color="#FF0000"> </font>text field will contain.)<br>
<br>
EASYRICH <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i><br>
Creates a rich text field using the simplest HCL C API functions <br>
(If you want to write a rich text field, read this sample first.)<br>
<br>
FONTBL <i>(Windows, AIX, IBM i, Linux RedHat)</i> <br>
Adds a font table to a document and writes some rich text to a rich text field, using fonts from the font table<br>
<br>
HISTORY (<i>Windows)</i><br>
Collects all response documents into the rich text field of the corresponding main document<br>
<br>
HOTSPOT <i>(Windows, AIX, Linux RedHat, IBM i)</i><br>
Creates a document with a popup, a button with formula, a bar, a URL, and a file attachment<br>
<br>
IMPORTER <i>(Windows)</i><br>
Imports graphics objects or word-processing files into a rich text field by calling a Notes import library<br>
<br>
JVAPPLET<i>(Windows, Linux RedHat, IBM i)</i><br>
Embed a Java applet in a rich text field in a document.<br>
<br>
LGIMPORT<i>(Windows)</i><br>
Imports large (&gt;64K) graphics objects or word-processing files into a rich text field<br>
(This sample calls a Notes import library and breaks the result into multiple rich text fields with the same name.)<br>
<br>
MKTABLE <i>(Windows, AIX, Linux RedHat, IBM i)</i> <br>
Adds a table to a rich text field, using the low-level structures of a table<br>
<br>
OLE2\ATTACH <i>(Windows)</i><br>
Embeds an OLE 2 object which has been streamed to a structured storage file into a rich text field of a document<br>
<br>
OLE2\EXTRACT <i>(Windows)</i><br>
Extracts embedded OLE 2 objects to structured storage files<br>
<br>
OLE2\OLEASSOC <i>(Windows)</i><br>
Associate file(s) with an embedded OLE 2 object.<br>
<br>
OLE2\DISASSOC <i>(Windows)</i><br>
Disassociate file(s) from an embedded OLE 2 object.<br>
<br>
OLE2\GETASSOC <i>(Windows)</i><br>
List file(s) associated with an embedded OLE 2 object.<br>
<br>
RRICH <i>(Windows, IBM i)</i> <br>
Reads a rich text field.<br>
<br>
WRICH <i>(</i><i>Windows, IBM i)</i> <br>
Creates a rich text field using low-level data structures <br>
(For advanced features of rich text fields, you will need to use these structures. The structures are statically allocated in this example, which is useful as a tutorial or if the rich text item you want to create will always be same.)<br>
<br>
<br>
<b><font size="5" color="#000080">Database Design</font></b><br>
<br>
These programs are in the <i>dbdesign</i> samples directory.<br>
<br>
ADDMACRO <i>(AIX, Linux RedHat, IBM i)</i> <br>
Adds several agents to a database - uses lower level functionality than the agents sample<br>
<br>
ADDQUERYARGS <i>(Windows, Linux)</i> <br>
Builds a various types of  input values to a Domino Query Language (DQL)<br>
<br>
AGENTS <i>(Windows, AIX, Linux RedHat, IBM i)</i><br>
Creates and executes several agent notes in a database<br>
<br>
DBPOLICY <i>(Windows)</i> <br>
Creates a database Policy Document (Help - About This Database document) and a database Help Document (Help - Using This Database document)<br>
<br>
DES_COLL <i>(Windows, AIX, Linux RedHat, IBM i)</i> <br>
Reads the design collection of any database and displays the type and name of each form, view, macro, and replication formula<br>
<br>
FORMULA <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i> <br>
Runs a formula against a note in a database, returning a value<br>
<br>
MAKEFORM <i>(</i><i>Windows, AIX, Linux RedHat, IBM i)</i><br>
Creates a new form in a database<br>
<br>
MAKENAV <i>(Windows, AIX , Linux RedHat, IBM i)</i> <br>
Creates a new navigator view and/or items in a database<br>
<br>
MAKEVIEW <i>(Windows, AIX, Linux RedHat, IBM i)</i> <br>
Creates a new view in a database<br>
<br>
NSFQUERY <i>(Windows, Linux)</i> <br>
Creates various types of queries and then uses them to query the database<br>
<br>
READFORM <i>(</i><i>Windows, AIX, Linux RedHat,  IBM i)</i> <br>
Reads the specified form note and displays a list of field names and data types<br>
<br>
READVIEW <i>(</i><i>Windows, AIX, Linux RedHat,  IBM i)</i> <br>
Reads the specified view note and displays information about the view<br>
<br>
RUNMACRO <i>(</i><i>Windows , IBM i)</i> <br>
Runs an agent in a database  - uses lower level functionality than the agents sample<br>
<br>
<br>
<b><font size="5" color="#000080">Administration</font></b><br>
<br>
These programs are in the <i>admin</i> samples directory.<br>
<br>
ACLS <i>(Windows, AIX, Linux RedHat,  IBM i)</i><br>
Reads in a database access control list, modifies it, and displays information contained in it<br>
<br>
ACTIVITY (<i>Windows, AIX, Linux RedHat,  </i><i>IBM i</i>)<br>
Illustrates usage of Activity Logging APIs.<br>
<br>
AUTH_FLD <i>(Windows, AIX, Linux RedHat,  IBM i)</i> <br>
Shows how to create document-level security fields<br>
<br>
BACKUP <i>(Windows)</i> <br>
Shows how to backup and restore databases, as well as archive transactional system logs<br>
<br>
DUSSPI <i>(Windows)</i> <br>
Illustrates Domino Upgrade Services<br>
<br>
FIND_DBS <i>(</i><i>Windows, IBM i, Linux)</i><br>
Finds all the Domino databases in a given local or remote directory<br>
<br>
LDAP_MSC <i>(Windows, IBM i, Linux)</i><br>
Adds, modifies, searches for and compares LDAP entries.<br>
<br>
PERFORM <i>(Windows, AIX, Linux RedHat,  IBM i)</i> <br>
Tests the performance of transactions such as database I/O and indexing on a Domino Directory<br>
<br>
PUTGET <i>( Windows, IBM i, Linux)</i> <br>
Data import and export tools<br>
(The directory includes source code, sample files, and a user guide. The tools are particularly useful for importing third-party data to a Domino database.)<br>
<br>
SECDOM <i>(Windows, AIX,IBM i, Linux)</i> <br>
Creates a DSAPI filter library that will, from the web, authenticate a Domino user through his Operating System account.
<ul></ul>
SEL_REP <i>(</i><i>Windows,IBM i)</i><br>
Creates a replication formula note to enable selective replication in a database<br>
<br>
SERVLIST <i>(</i><i>Windows)</i> <br>
Finds all the available HCL Domino Servers listed in the user's home/mail server's Domino Directory.<br>
<br>
SETPRIVS <i>(</i><i>Windows, IBM i, Linux)</i> <br>
Sets the read access privilege levels or read access name list of all documents in a database<br>
<br>
TRACKER <i>(Windows, IBM i)</i> <br>
Demonstrates capabilities of a Note Open/Note Update Hook Driver<br>
(TRACKER logs all access to a database, writes a &quot;Request Number&quot; field to new documents when they are saved, and saves documents to a &quot;trash can&quot; database when they are deleted.)<br>
<br>
USERREG <i>(</i><i>Windows, AIX, IBM i, Linux RedHat)</i><br>
Illustrates how to register a new hierarchical certifier, server, and user<br>
<br>
<br>
<b><font size="5" color="#000080">Server</font></b><br>
<br>
These programs are in the <i>server</i> samples directory.<br>
<br>
ADDIN <i>(</i><i>Windows, AIX,  IBM i, Linux RedHat )</i><br>
Shows the structure of a HCL C API add-in task for a HCL Domino Server<br>
(This version uses &quot;Text&quot; functions instead of application resources.)<br>
<br>
ADD_RES <i>(</i><i>Windows, IBM i, Linux)</i><br>
Shows the structure of a HCL C API add-in task for a HCL Domino Server<br>
(This version uses application resources.)<br>
<br>
EVENTS (<i>Windows, IBM i</i>, <i>Linux</i>) <br>
Demonstrates user-defined events<br>
<br>
MGATE (<i>Windows</i>) <br>
A sample mail gateway<br>
<br>
MSG_Q <i>(Windows, IBM i, Linux)</i> <br>
Demonstrates sending messages from the server console to an add-in task via a message queue<br>
Includes an additional add-in task MSG_T that sends messages directly to the MSG_Q task<br>
<br>
STATDEMO (<i>Windows, </i> IBM i, <i>Linux</i>) <br>
Periodically updates a database with information from the statistics reporting routines<br>
<br>
THREADS (<i>Windows, AIX,  Linux RedHat,  IBM i)</i><br>
Demonstrates multi-threaded API program support within the structure of an add-in task and uses message queues for thread communication<br>
<br>
<br>
<b><font size="5" color="#000080">Mail</font></b><br>
<br>
These programs are in the <i>mail</i> samples directory.<br>
<br>
EXTMAIL <i>(Windows)</i><br>
Implements an extension manager that traps a user mail message, modifies the body of the message, and then sends the user mail information and a log file of C API processing.<br>
<br>
NAMEBOOK <i>(Windows, IBM i, Linux)</i><br>
Lists all  Address books identified by the NAMES variable in the notes.ini file.<br>
<br>
READMAIL <i>(Windows, AIX, IBM i, Linux RedHat)</i><br>
Prints the contents of a message (mail) file using Mail Gateway C API functions.<br>
<br>
SENDMAIL <i>(</i><i>Windows, IBM i, Linux)</i><br>
Sends a mail memo using Mail Gateway C API functions.<br>
<br>
SENDMEMO <i>(</i><i>Windows, IBM i, Linux)</i><br>
Sends a memo using NSF C API functions.<br>
<br>
MAILCERT <i>(Windows, IBM i, Linux)</i><br>
Demonstrate how to enumerate certificates in a S/MIME mail.<br>
<br>
SENDEASYMM<i>(Windows, IBM i, Linux)</i><br>
Demonstrate how to create a easy MIME(Multipurpose Internet Mail Extensions) message.<br>
<br>
SENDATTMM<i>(Windows, IBM i, Linux)</i><br>
Demonstrate how to create a MIME(Multipurpose Internet Mail Extensions) message with embedded attachment.<br>
<br>
READMMTXT<i>(Windows, IBM i, Linux)</i><br>
Demonstrate how to get the text contents from the MIME messages without converting them to CD format.<br>
<br>
PARSEMMMSG<i>(Windows, IBM i, Linux)</i><br>
Demonstrate how to parse the structure of the MIME messages<br>
<br>
<b><font size="5" color="#000080">Miscellaneous</font></b><br>
<br>
These programs are in the <i>misc</i> samples directory.<br>
<br>
ALARM<i> </i><i>(Windows)</i><br>
Demonstates the Alarm C API functionality<br>
<br>
DBDRIVE <i>(Windows,  IBM i)</i><br>
Implements a driver DLL that allows Domino or Notes to access data in non-Domino databases using the functions @DbLookup and @DbColumn<br>
<br>
EDITFAX<i> (Windows)</i><br>
Demonstates the usage of the editfax APIs.<br>
<br>
ENCRYPT <i>(</i><i>Windows,IBM i)</i> <br>
Demonstrates how to write encryption enabled fields as well as how to read and store encrypted documents in a database, using secret and public encryption keys.<br>
<br>
EXTCONF <i>(Windows, IBM i)</i><br>
Implements an extension manager that handles replication conflicts<br>
<br>
EXTMNGR <i>(</i><i>Windows, IBM i)</i><br>
Implements an extension manager that transforms an existing non-Domino database into a Domino database at Domino database creation time<br>
<br>
EXTPWD <i>(Windows, AIX, Linux RedHat,  IBM i)</i> <br>
Demonstrates using the Extension Manager to replace the password dialog<br>
<br>
FILEATT <i>(Windows, AIX, IBM i, Linux RedHat)</i><br>
Creates a document with file attachments with no corresponding hotspots<br>
<br>
FTSEARCH <i>(Windows, IBM i, Linux) </i><br>
Demonstrates full-text searching capabilities<br>
<br>
GETMULTNOTEINFO  <i>(Windows, Windows 64-bit, AIX 32-bit, AIX 64-bit Linux Suse 32bit, IBM i, Linux)</i> <br>
Shows the basic usage of NSFDbGetMultNoteInfo &amp; NSFDbGetMultNoteInfoByUNID.<br>
<br>
IDBACKUP <i>(Windows, IBM i) </i><br>
Demonstrates Notes ID backup and recovery <br>
<br>
IDTABLES <i>( Windows, IBM i, Linux)</i> <br>
Shows how to use ID Tables for various operations with note IDs. also demonstrates operations between the tables. <br>
(ID tables are an efficient method for processing a large set of notes at once.)<br>
<br>
ITEMMISC <i>( Windows, Linux)</i> <br>
This program changes an item value in a document and then copies the item to another document in the same view and renames it. It also checks that the documents in the view have a $Readers field<br>
<br>
NIF <i>(Windows, Linux)</i> <br>
Demonstrates the usage of Notes Indexing Facility (NIF) related API calls. Checks whether the view in a database is time-varying,adds a document and checks whetherthe collection is up-to-date, and the note ID is in the view,read view entries and data associated with them, gets the last modified time of the database. It alsogets view rebuild directorypath. <br>
<br>
NOTECWF <i>(Windows, IBM i, Linux)</i> <br>
Demonstrates NSFNoteComputeWithForm C API function and validation error callback function<br>
<br>
NOTESFLO <i>(Windows)</i><br>
Demonstrates Notes Field Exchange (Notes/FX) and NotesFlow in a COM/OLE 2 program<br>
<br>
NSF_DUMP <i>(Windows, AIX,  Linux RedHat,  IBM i)</i> <br>
Displays the contents of a database file<br>
<br>
RESPONSE <i>(</i><i>Windows, Linux)</i> <br>
Creates and reads the response documents. It also updates the change in unread documents to the remote server.<br>
<br>
SCHEDULE<i>(Windows,IBM i, Linux)</i> <br>
Demonstrates adding appointments and meeting invitations to a User's schedule as well as deleting the scheduled events  and retrieving busy/free time information<br>
<br>
UNREAD <i>(Windows, AIX, Linux RedHat,  IBM i)</i><br>
Demonstrates obtaining and modifying a table of unread notes for a user in a database file<br>
<br>
USER_DEF <i>(Windows, AIX, Linux RedHat,  IBM i) </i><br>
Shows how to create and read fields with user-defined data types<br>
(These fields are useful for storing special objects of your own creation, such as new kinds of graphics, data encrypted with your own scheme, and so on.)<br>
<br>
XML\EXPORT (<i>Windows, IBM i)</i><br>
Illustrates the DXL Export functionality for exporting Domino/Notes data into XML format.<br>
<br>
XML\IMPORT<i> (Windows, IBM i, Linux)</i><br>
Illustrates the DXL Import functionality for importing XML data into Domino/Notes data.<br>
<br>
ARCHSVC\ARCHEXP<i> (Windows, AIX,  Linux RedHat,  IBM i)</i><br>
Illustrates the archive export functionality for export a data note from db into output file.<br>
<br>
ARCHSVC\ARCHIMP<i> (Windows, AIX,  Linux RedHat,  IBM i)</i><br>
Illustrates the archive import functionality for import the archived file to the specified note and restore the note back to the db.<br>
<br>
<b><font size="5" color="#000080">Advanced Server</font></b><br>
<br>
These programs are in the <i>advsrvr</i> samples directory.<br>
<br>
BILLING<i>(Windows, AIX, IBM i)</i><br>
Customized Billing add-in and Billing manager samples<br>
<br>
CLUSTER<i>(Windows, AIX,IBM i)</i><br>
Illustrates features of Advanced Server Clusters<br>
(The CLUMON sample supports the administrative tasks associated with viewing server clusters and clustered databases and with updating server restrictions, availability, and database mark options.)<br>
<br>
<br>
<b><font size="5" color="#000080">Client</font></b><br>
<br>
These programs are in the <i>client</i> samples directory.<br>
<br>
IEDIT <i>(Windows)</i> <br>
Creates a custom edit-level import library<br>
<br>
UIADDIN\UIADDIN1 <i>(Windows)</i><br>
Illustrates how to implement the Notes menu add-in feature<br>
(Menu add-ins are user-written DLLs that add menu items to the Actions menu in Notes and provide procedures to handle each menu item.)<br>
<br>
UIADDIN\UIADDIN2 <i>(Windows) </i><br>
Demonstrates more complicated Notes menu add-in features<br>
(This sample adds multiple menu items to the Actions menu in Notes and demonstrates how to import data into a field of an open document.)<br>
<br>
XEDIT <i>(Windows)</i><br>
Creates a custom edit-level export library<br>
<br>
XVIEW <i>(Windows)</i><br>
Creates a custom view-level export library<br>
<br>
<b><font size="5" color="#000080">D</font></b><b><font size="5" color="#000080">B2</font></b><br>
<br>
These programs are in the <i>DB2</i> samples directory.<br>
<br>
NSFDB2FCopy <i>(Windows) </i><br>
Copy the NSFDB2 database specified and reconnects the copy of the DB2 data as an NSFDB2 database.<br>
<br>
NSFDB2FList <i>(Windows) </i><br>
Provides a list of all NSFDB2 databases.<br>
<br>
NSFDB2ReCon <i>(Windows) </i><br>
Make sure that Domino can access NSFDB2 data for FullPath or rename the NSFDB2 database within the Domino server.<br>
<br>
<br>
<b><font size="5" color="#000080">HTML</font></b><br>
<br>
These programs are in the <i>html</i> samples directory.<br>
<br>
ConvertAttach <i>(Windows, IBM i) </i><br>
Building a program which can be used to convert an attachment file which can be used in HTML format.<br>
<br>
ConvertNormal<i> (Windows, IBM i) </i><br>
Example of convertting an attachment to be HTML format<br>
<br>
ConvertPic<i> (Windows, IBM i) </i><br>
Example of convertting an attachment to be HTML format<br>
<br>
<br>
<b><font size="5" color="#000080">Calapi</font></b><br>
<br>
These programs are in the calapi samples directory.<br>
<br>
entryManip <i>(Windows, IBM i, Linux) </i><br>
Example of create, update, read, delete entries on iCalendar format<br>
<br>
entryAction (Windows, IBM i, <i>Linux</i>)<br>
Example of entry actions on iCalendar format<br>
<br>
<br>
<b><font size="5" color="#000080">TIME</font></b><br>
<br>
These programs are in the time samples directory.<br>
<br>
GMT <i>(Windows, Linux) </i><br>
Explains the usage ofextracting ticks and date fromTIMEDATE structure.Alsodescribesusageof GMTtolocal time andvicea versa.<br>
<br>
TIMEDATEPAIR <i>(Windows, Linux) </i><br>
Thisprogramdemonstratesthe usage of,<br>
ConvertTIMEDATEPAIRToText- Converts TIMEDATEPAIR to text format<br>
ConvertTextToTIMEDATEPAIR- Converts Text to TIMEDATEPAIR<br>
This program gets the current date and time and adds one day to itto form the text form of time date pair. It usesConvertTextToTIMEDATEPAIRAPI to convert text into time date pair object.<br>
It uses the time date pair object, which populatedearlierto demonstrateon converting time date pair object to text usingConvertTIMEDATEPAIRToTextAPI.<br>
<br>
TIMETEST <i>(Windows, Linux) </i><br>
Thisprogramdemonstratesthe usage of,<br>
TimeDateCollate- Compares two binary TIMEDATE values.<br>
TimeExtractJulianDate - Extracts the Julian date from a TIMEDATE value. <br>
TimeDateDifferenceFloat - Gives the Floating-point difference between two TIMEDATE values.<font face="Calibri"></font><font size="4"> </font><br>
<br>
<b><font size="5" color="#000080">OS</font></b><br>
<br>
These programs are in the os samples directory.<br>
<br>
ENVIRONMENT <i>(Windows, Linux) </i><br>
Demonstrates how toset atimedateinto an environment variableandgetatimedatefromthe environment variable and returns a sequence number that represents the number of times any environment variable has been changed.Here the sequence number changing means the notes.ini file has been changed.If our variable isdynamic,then we can also check if our variable has changed or not.<br>
<br>
SHAREDIRECTORY <i>(Windows, Linux)</i><br>
Demonstrates how to print the path of the shared directory of a multi-user Notes client.

NOTE: For V14.0, the supported build platforms are Windows & Linux 64bit.

---
