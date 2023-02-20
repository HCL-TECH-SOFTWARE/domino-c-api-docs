##### Chapter 2-3
##### Sample Programs

**Overview**   

The HCL C API Toolkit for Domino and Notes contains many sample programs that show you how to use various aspects of the C API. The samples are divided into the following groups:  

**Administration**   
Programs that show how to perform Domino system administration operations like controlling database access and checking server performance  

**Advanced Server**   
Programs that illustrate how to use the C API to develop applications that manage clustered servers and databases and implement customized billing managers and add-in tasks  

**Basic**   
Programs that show the basic structure of API code or basic operations using the C API  

**Client**   
Programs that show the structure of client specific API code or operations using the C API  

**Database Design**   
Programs that show how to create and read database design elements, including forms, views, navigators, agents, access control lists, and policy and help documents  

**DB2**   
Programs that show the structure of DB2 specific API code  

**Mail**   
Programs that show how to use the C API for electronic mail operations, such as sending and receiving mail and writing mail gateways  

**Miscellaneous**   
Programs that show various C API operations not covered by the other samples  

**Rich Text**   
Programs that show how to read and write elements of a rich text field  

**Server**   
Programs that show the structure of HCL Domino Server add-in tasks and features of the HCL Domino Server environment  

**Views**   
Programs that show how to use indexes (views)  

**HTML**   
Programs that show how to use HTML functions  

**CALAPI**   
Programs that show how to use iCalendar functions  

**OS**   
Programs that show how to use C API for OS operations.  

**TIME**   
Program that shows how to use time conversion operations.  

The sample descriptions below indicate the platforms each sample supports. Some samples do not support all platforms, but each sample contains valuable code relevant to all platforms. HCL C API functions for Domino and Notes are largely the same on every platform. Frequently, only the makefile varies from platform to platform.  

Note that the sample programs use the minimum stack sizes necessary for execution. Other applications may require larger stack sizes.   

<br />

**Basic**   

These programs are in the *basic* samples directory.  

ALLFLDS *(* *Windows, AIX, Linux RedHat, IBM i)*   
Finds all the fields in all the documents in a database  

CAPIERR (*Windows* )  
Shows how to load an error message string given a Domino or Notes error code, from a Windows MFC C++ application.  

COPYDB *(* *Windows, AIX, Linux RedHat, IBM i)*   
Copies all the components of one database to another  

CPNOTES *(* *Windows, AIX, Linux RedHat, IBM i)*   
Selectively copies documents from one database to another based on various criteria, including modification time  

DBPROPS (*Windows* , IBM i, *Linux* )  
Shows how to get and set some of the database properties available to the HCL C API.  

GETBUILD *(* *Windows, AIX, Linux RedHat, IBM i)*   
Shows how to get the major build number identifying the version of Domino or Notes installed  

INTRO *(* *Windows, AIX, Linux RedHat, IBM i)*   
Shows the basic structure of a character-mode HCL C API program, as well as how to access a database that is on a remote HCL Domino Server. Uses main as the main entry point.  

INTROWIN *(* *Windows)*   
Shows the basic structure of a Windows application that makes HCL C API calls  

MSIMPLE *(* *Windows, AIX, Linux RedHat, IBM i)*   
Modifies fields with simple data types  

NOTESMAIN *(Windows, AIX, IBM i, Linux RedHat, )*   
Shows the basic structure of a character-mode HCL C API program, as well as how to access a database that is on a remote HCL Domino Server. Uses NotesMain as the main entry point.   

NUMLIST *(* *Windows, AIX, Linux RedHat, IBM i)*   
Writes a field of type number list  

RSIMPLE *(Windows, AIX, Linux RedHat, IBM i)*   
Reads fields with simple data types   
(This sample demonstrates a basic sequential search of a database.)  

SRCH_ALL *(* *Windows, AIX, Linux RedHat, IBM i)*   
Search for and process all documents in a database  
(This sample shows how to guarantee that each document is only processed once during a sequential search.)  

SUMMARY *(* *Windows, AIX, Linux RedHat, IBM i)*   
Finds and prints all summary data of all data notes in a database, without opening the data notes  

WSIMPLE *(* *Windows, AIX, Linux RedHat, IBM i)*   
Writes fields with simple data types: text, number, date/time, text list  

sizeofHANDLE *(Windows, IBM i)*   
Show length of some HANDLEs  

**Views**   

These programs are in the *views* samples directory.  

NAMELOOK *(* *Windows, IBM i, Linux)*   
Look up names in the Personal Address book and retrieve items  

NAVIGATE *(* *Windows, IBM i, Linux)*   
Performs complex navigation of a view index  

ONECAT *(* *Windows, IBM i, Linux)*   
Lists all the documents in one category in a view  

TEXTKEY *(* *Windows, IBM i, Linux)*   
Finds documents in a view based on a single text key  

TWOKEY (*Windows, AIX, IBM i, Linux RedHat* )   
Finds documents in a view based on two sort keys of different data types  

VIEWIDS *(Windows, AIX,Linux RedHat, IBM i)*   
Finds all the documents in a view and lists their note IDs  

VIEWSUMM *(* *Windows, AIX, Linux RedHat, IBM i)*   
Prints the summary information in a view   
(This program essentially duplicates a view as you see it at the user interface. The view summary is useful because it allows you to extract fields from the documents in a view without opening the documents.)  

<br />

**Rich Text**   

These programs are in the *richtext* samples directory.  

BIG_RICH *(* *Windows, Linux)*   
Creates rich text fields from character text files up to five megabytes long using Compound Text functions  

CDFILE *(* *Windows, AIX, Linux RedHat, IBM i)*   
Two programs to read and write a rich text (CD) file: CDFWRITE writes text to a CD file, and CDFREAD reads a CD file and stores it in the rich text field of a document  

DOCLINK *(* *Windows, IBM i)*   
Adds a document link, a view link and a database link to a rich text field, using the low-level structures of a document, view and database link  

DUMPFONT *(Windows, AIX, Linux RedHat, IBM i)*   
Locates and prints out the font tables in all data notes  

DYNAMIC *(* *Windows, AIX, Linux RedHat, IBM i)*   
Same as WRICH, but uses dynamic allocation of the data structures  
(This technique is useful if you do not know at compile time exactly what the rich text field will contain.)  

EASYRICH *(* *Windows, AIX, Linux RedHat, IBM i)*   
Creates a rich text field using the simplest HCL C API functions   
(If you want to write a rich text field, read this sample first.)  

FONTBL *(Windows, AIX, IBM i, Linux RedHat)*   
Adds a font table to a document and writes some rich text to a rich text field, using fonts from the font table  

HISTORY (*Windows)*   
Collects all response documents into the rich text field of the corresponding main document  

HOTSPOT *(Windows, AIX, Linux RedHat, IBM i)*   
Creates a document with a popup, a button with formula, a bar, a URL, and a file attachment  

IMPORTER *(Windows)*   
Imports graphics objects or word-processing files into a rich text field by calling a Notes import library  

JVAPPLET*(Windows, Linux RedHat, IBM i)*   
Embed a Java applet in a rich text field in a document.  

LGIMPORT*(Windows)*   
Imports large (\>64K) graphics objects or word-processing files into a rich text field  
(This sample calls a Notes import library and breaks the result into multiple rich text fields with the same name.)  

MKTABLE *(Windows, AIX, Linux RedHat, IBM i)*   
Adds a table to a rich text field, using the low-level structures of a table  

OLE2\\ATTACH *(Windows)*   
Embeds an OLE 2 object which has been streamed to a structured storage file into a rich text field of a document  

OLE2\\EXTRACT *(Windows)*   
Extracts embedded OLE 2 objects to structured storage files  

OLE2\\OLEASSOC *(Windows)*   
Associate file(s) with an embedded OLE 2 object.  

OLE2\\DISASSOC *(Windows)*   
Disassociate file(s) from an embedded OLE 2 object.  

OLE2\\GETASSOC *(Windows)*   
List file(s) associated with an embedded OLE 2 object.  

RRICH *(Windows, IBM i)*   
Reads a rich text field.  

WRICH *(* *Windows, IBM i)*   
Creates a rich text field using low-level data structures   
(For advanced features of rich text fields, you will need to use these structures. The structures are statically allocated in this example, which is useful as a tutorial or if the rich text item you want to create will always be same.)  

<br />

**Database Design**   

These programs are in the *dbdesign* samples directory.  

ADDMACRO *(AIX, Linux RedHat, IBM i)*   
Adds several agents to a database - uses lower level functionality than the agents sample  

ADDQUERYARGS *(Windows, Linux)*   
Builds a various types of input values to a Domino Query Language (DQL)  

AGENTS *(Windows, AIX, Linux RedHat, IBM i)*   
Creates and executes several agent notes in a database  

DBPOLICY *(Windows)*   
Creates a database Policy Document (Help - About This Database document) and a database Help Document (Help - Using This Database document)  

DES_COLL *(Windows, AIX, Linux RedHat, IBM i)*   
Reads the design collection of any database and displays the type and name of each form, view, macro, and replication formula  

FORMULA *(* *Windows, AIX, Linux RedHat, IBM i)*   
Runs a formula against a note in a database, returning a value  

MAKEFORM *(* *Windows, AIX, Linux RedHat, IBM i)*   
Creates a new form in a database  

MAKENAV *(Windows, AIX , Linux RedHat, IBM i)*   
Creates a new navigator view and/or items in a database  

MAKEVIEW *(Windows, AIX, Linux RedHat, IBM i)*   
Creates a new view in a database  

NSFQUERY *(Windows, Linux)*   
Creates various types of queries and then uses them to query the database  

READFORM *(* *Windows, AIX, Linux RedHat, IBM i)*   
Reads the specified form note and displays a list of field names and data types  

READVIEW *(* *Windows, AIX, Linux RedHat, IBM i)*   
Reads the specified view note and displays information about the view  

RUNMACRO *(* *Windows , IBM i)*   
Runs an agent in a database - uses lower level functionality than the agents sample  

<br />

**Administration**   

These programs are in the *admin* samples directory.  

ACLS *(Windows, AIX, Linux RedHat, IBM i)*   
Reads in a database access control list, modifies it, and displays information contained in it  

ACTIVITY (*Windows, AIX, Linux RedHat,* *IBM i* )  
Illustrates usage of Activity Logging APIs.  

AUTH_FLD *(Windows, AIX, Linux RedHat, IBM i)*   
Shows how to create document-level security fields  

BACKUP *(Windows)*   
Shows how to backup and restore databases, as well as archive transactional system logs  

DUSSPI *(Windows)*   
Illustrates Domino Upgrade Services  

FIND_DBS *(* *Windows, IBM i, Linux)*   
Finds all the Domino databases in a given local or remote directory  

LDAP_MSC *(Windows, IBM i, Linux)*   
Adds, modifies, searches for and compares LDAP entries.  

PERFORM *(Windows, AIX, Linux RedHat, IBM i)*   
Tests the performance of transactions such as database I/O and indexing on a Domino Directory  

PUTGET *( Windows, IBM i, Linux)*   
Data import and export tools  
(The directory includes source code, sample files, and a user guide. The tools are particularly useful for importing third-party data to a Domino database.)  

SECDOM *(Windows, AIX,IBM i, Linux)*   
Creates a DSAPI filter library that will, from the web, authenticate a Domino user through his Operating System account.

SEL_REP *(* *Windows,IBM i)*   
Creates a replication formula note to enable selective replication in a database  

SERVLIST *(* *Windows)*   
Finds all the available HCL Domino Servers listed in the user's home/mail server's Domino Directory.  

SETPRIVS *(* *Windows, IBM i, Linux)*   
Sets the read access privilege levels or read access name list of all documents in a database  

TRACKER *(Windows, IBM i)*   
Demonstrates capabilities of a Note Open/Note Update Hook Driver  
(TRACKER logs all access to a database, writes a "Request Number" field to new documents when they are saved, and saves documents to a "trash can" database when they are deleted.)  

USERREG *(* *Windows, AIX, IBM i, Linux RedHat)*   
Illustrates how to register a new hierarchical certifier, server, and user  

<br />

**Server**   

These programs are in the *server* samples directory.  

ADDIN *(* *Windows, AIX, IBM i, Linux RedHat )*   
Shows the structure of a HCL C API add-in task for a HCL Domino Server  
(This version uses "Text" functions instead of application resources.)  

ADD_RES *(* *Windows, IBM i, Linux)*   
Shows the structure of a HCL C API add-in task for a HCL Domino Server  
(This version uses application resources.)  

EVENTS (*Windows, IBM i* , *Linux* )   
Demonstrates user-defined events  

MGATE (*Windows* )   
A sample mail gateway  

MSG_Q *(Windows, IBM i, Linux)*   
Demonstrates sending messages from the server console to an add-in task via a message queue  
Includes an additional add-in task MSG_T that sends messages directly to the MSG_Q task  

STATDEMO (*Windows,* IBM i, *Linux* )   
Periodically updates a database with information from the statistics reporting routines  

THREADS (*Windows, AIX, Linux RedHat, IBM i)*   
Demonstrates multi-threaded API program support within the structure of an add-in task and uses message queues for thread communication  

<br />

**Mail**   

These programs are in the *mail* samples directory.  

EXTMAIL *(Windows)*   
Implements an extension manager that traps a user mail message, modifies the body of the message, and then sends the user mail information and a log file of C API processing.  

NAMEBOOK *(Windows, IBM i, Linux)*   
Lists all Address books identified by the NAMES variable in the notes.ini file.  

READMAIL *(Windows, AIX, IBM i, Linux RedHat)*   
Prints the contents of a message (mail) file using Mail Gateway C API functions.  

SENDMAIL *(* *Windows, IBM i, Linux)*   
Sends a mail memo using Mail Gateway C API functions.  

SENDMEMO *(* *Windows, IBM i, Linux)*   
Sends a memo using NSF C API functions.  

MAILCERT *(Windows, IBM i, Linux)*   
Demonstrate how to enumerate certificates in a S/MIME mail.  

SENDEASYMM*(Windows, IBM i, Linux)*   
Demonstrate how to create a easy MIME(Multipurpose Internet Mail Extensions) message.  

SENDATTMM*(Windows, IBM i, Linux)*   
Demonstrate how to create a MIME(Multipurpose Internet Mail Extensions) message with embedded attachment.  

READMMTXT*(Windows, IBM i, Linux)*   
Demonstrate how to get the text contents from the MIME messages without converting them to CD format.  

PARSEMMMSG*(Windows, IBM i, Linux)*   
Demonstrate how to parse the structure of the MIME messages  

**Miscellaneous**   

These programs are in the *misc* samples directory.  

ALARM*(Windows)*   
Demonstates the Alarm C API functionality  

DBDRIVE *(Windows, IBM i)*   
Implements a driver DLL that allows Domino or Notes to access data in non-Domino databases using the functions @DbLookup and @DbColumn  

EDITFAX*(Windows)*   
Demonstates the usage of the editfax APIs.  

ENCRYPT *(* *Windows,IBM i)*   
Demonstrates how to write encryption enabled fields as well as how to read and store encrypted documents in a database, using secret and public encryption keys.  

EXTCONF *(Windows, IBM i)*   
Implements an extension manager that handles replication conflicts  

EXTMNGR *(* *Windows, IBM i)*   
Implements an extension manager that transforms an existing non-Domino database into a Domino database at Domino database creation time  

EXTPWD *(Windows, AIX, Linux RedHat, IBM i)*   
Demonstrates using the Extension Manager to replace the password dialog  

FILEATT *(Windows, AIX, IBM i, Linux RedHat)*   
Creates a document with file attachments with no corresponding hotspots  

FTSEARCH *(Windows, IBM i, Linux)*   
Demonstrates full-text searching capabilities  

GETMULTNOTEINFO *(Windows, Windows 64-bit, AIX 32-bit, AIX 64-bit Linux Suse 32bit, IBM i, Linux)*   
Shows the basic usage of NSFDbGetMultNoteInfo \& NSFDbGetMultNoteInfoByUNID.  

IDBACKUP *(Windows, IBM i)*   
Demonstrates Notes ID backup and recovery   

IDTABLES *( Windows, IBM i, Linux)*   
Shows how to use ID Tables for various operations with note IDs. also demonstrates operations between the tables.   
(ID tables are an efficient method for processing a large set of notes at once.)  

ITEMMISC *( Windows, Linux)*   
This program changes an item value in a document and then copies the item to another document in the same view and renames it. It also checks that the documents in the view have a $Readers field  

NIF *(Windows, Linux)*   
Demonstrates the usage of Notes Indexing Facility (NIF) related API calls. Checks whether the view in a database is time-varying, adds a document and checks whether the collection is up-to-date, and the note ID is in the view, read view entries and data associated with them, gets the last modified time of the database. It also gets view rebuild directory path.   

NOTECWF *(Windows, IBM i, Linux)*   
Demonstrates NSFNoteComputeWithForm C API function and validation error callback function  

NOTESFLO *(Windows)*   
Demonstrates Notes Field Exchange (Notes/FX) and NotesFlow in a COM/OLE 2 program  

NSF_DUMP *(Windows, AIX, Linux RedHat, IBM i)*   
Displays the contents of a database file  

RESPONSE *(* *Windows, Linux)*   
Creates and reads the response documents. It also updates the change in unread documents to the remote server.  

SCHEDULE*(Windows,IBM i, Linux)*   
Demonstrates adding appointments and meeting invitations to a User's schedule as well as deleting the scheduled events and retrieving busy/free time information  

UNREAD *(Windows, AIX, Linux RedHat, IBM i)*   
Demonstrates obtaining and modifying a table of unread notes for a user in a database file  

USER_DEF *(Windows, AIX, Linux RedHat, IBM i)*   
Shows how to create and read fields with user-defined data types  
(These fields are useful for storing special objects of your own creation, such as new kinds of graphics, data encrypted with your own scheme, and so on.)  

XML\\EXPORT (*Windows, IBM i)*   
Illustrates the DXL Export functionality for exporting Domino/Notes data into XML format.  

XML\\IMPORT*(Windows, IBM i, Linux)*   
Illustrates the DXL Import functionality for importing XML data into Domino/Notes data.  

ARCHSVC\\ARCHEXP*(Windows, AIX, Linux RedHat, IBM i)*   
Illustrates the archive export functionality for export a data note from db into output file.  

ARCHSVC\\ARCHIMP*(Windows, AIX, Linux RedHat, IBM i)*   
Illustrates the archive import functionality for import the archived file to the specified note and restore the note back to the db.  

**Advanced Server**   

These programs are in the *advsrvr* samples directory.  

BILLING*(Windows, AIX, IBM i)*   
Customized Billing add-in and Billing manager samples  

CLUSTER*(Windows, AIX,IBM i)*   
Illustrates features of Advanced Server Clusters  
(The CLUMON sample supports the administrative tasks associated with viewing server clusters and clustered databases and with updating server restrictions, availability, and database mark options.)  

<br />

**Client**   

These programs are in the *client* samples directory.  

IEDIT *(Windows)*   
Creates a custom edit-level import library  

UIADDIN\\UIADDIN1 *(Windows)*   
Illustrates how to implement the Notes menu add-in feature  
(Menu add-ins are user-written DLLs that add menu items to the Actions menu in Notes and provide procedures to handle each menu item.)  

UIADDIN\\UIADDIN2 *(Windows)*   
Demonstrates more complicated Notes menu add-in features  
(This sample adds multiple menu items to the Actions menu in Notes and demonstrates how to import data into a field of an open document.)  

XEDIT *(Windows)*   
Creates a custom edit-level export library  

XVIEW *(Windows)*   
Creates a custom view-level export library  

**D** **B2**   

These programs are in the *DB2* samples directory.  

NSFDB2FCopy *(Windows)*   
Copy the NSFDB2 database specified and reconnects the copy of the DB2 data as an NSFDB2 database.  

NSFDB2FList *(Windows)*   
Provides a list of all NSFDB2 databases.  

NSFDB2ReCon *(Windows)*   
Make sure that Domino can access NSFDB2 data for FullPath or rename the NSFDB2 database within the Domino server.  

<br />

**HTML**   

These programs are in the *html* samples directory.  

ConvertAttach *(Windows, IBM i)*   
Building a program which can be used to convert an attachment file which can be used in HTML format.  

ConvertNormal*(Windows, IBM i)*   
Example of convertting an attachment to be HTML format  

ConvertPic*(Windows, IBM i)*   
Example of convertting an attachment to be HTML format  

<br />

**Calapi**   

These programs are in the calapi samples directory.  

entryManip *(Windows, IBM i, Linux)*   
Example of create, update, read, delete entries on iCalendar format  

entryAction (Windows, IBM i, *Linux* )  
Example of entry actions on iCalendar format  

<br />

**TIME**   

These programs are in the time samples directory.  

GMT *(Windows, Linux)*   
Explains the usage of extracting ticks and date from TIMEDATE structure. Also describes usage of GMT to local time and vice a versa.  

TIMEDATEPAIR *(Windows, Linux)*   
This program demonstrates the usage of,   
ConvertTIMEDATEPAIRToText - Converts TIMEDATEPAIR to text format   
ConvertTextToTIMEDATEPAIR - Converts Text to TIMEDATEPAIR   
This program gets the current date and time and adds one day to it to form the text form of time date pair. It uses ConvertTextToTIMEDATEPAIR API to convert text into time date pair object.   
It uses the time date pair object, which populated earlier to demonstrate on converting time date pair object to text using ConvertTIMEDATEPAIRToText API.  

TIMETEST *(Windows, Linux)*   
This program demonstrates the usage of,   
TimeDateCollate - Compares two binary TIMEDATE values.   
TimeExtractJulianDate - Extracts the Julian date from a TIMEDATE value.   
TimeDateDifferenceFloat - Gives the Floating-point difference between two TIMEDATE values.   

**OS**   

These programs are in the os samples directory.  

ENVIRONMENT *(Windows, Linux)*   
Demonstrates how to set a timedate into an environment variable and get a timedate from the environment variable and returns a sequence number that represents the number of times any environment variable has been changed. Here the sequence number changing means the notes.ini file has been changed. If our variable is dynamic, then we can also check if our variable has changed or not.  

SHAREDIRECTORY *(Windows, Linux)*   
Demonstrates how to print the path of the shared directory of a multi-user Notes client.
---
