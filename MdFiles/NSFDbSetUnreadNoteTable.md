




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
 /\* List Definitions \*/
 ol
 {margin-bottom:0cm;}
ul
 {margin-bottom:0cm;}
-->




**Initial Release 3.4**



**Function : Unread Notes**



**NSFDbSetUnreadNoteTable** **- Store
list of unread notes for user**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbSetUnreadNoteTable(**  

      DBHANDLE  hDB,  

      char far \*UserName,  

      WORD  UserNameLength,  

      BOOL  fFlushToDisk,  

      DHANDLE  hOriginalUnreadList,  

      DHANDLE  hUnreadUnreadList**);**



**Description :**



This
function merges changes between the original ID table and the modified table
into the specified user's unread note list for the database.  After this call
completes, both the original unread table and the supplied unread table are
updated to reflect the current state of the unread note list for the database. 
Prior to Release 4.5 of Notes, this function will only work with local
databases.  If both the server and the workstation have Release 4.5 or later of
Domino and Notes installed, this function will also work with remote databases.  

  

The user name must be the complete user name, as it would be retrieved from the
user's ID file.  In particular, if the name is hierarchical, the user name
string must be the fully distinguished hierarchical user name.  This form of
the name can be obtained by calling DNCanonicalize().  

  

In normal operation, updates to the unread note list are buffered in memory. 
The flag fFlushToDisk may be set to TRUE to write the updates immediately to
disk.


 


In general,
you should:


1.      After
calling NSFDbGetUnreadNoteTable, always execute NSFDbUpdateUnread to update the
cached unread list as well as the unread list in the database, so they will
reflect the changes made to the database (i.e. document adds/deletes, etc.)
after the last time the unread list was saved in the database.


2.      Always
specify a "point of divergence", which will be used as the
hOriginalUnreadList argument to NSFDbSetUnreadNoteTable.  The "point of
divergence" should be created (by calling IDTableCopy) AFTER the calling
of NSFDbUpdateUnread to reflect the updated version of the unread list.


3.      After
calling NSFDbUpdateUnread, if a copy of the "point of divergence"
existed already, always re-establish a new copy of the "point of
divergence" by deleting the old "point of divergence" IDTable
(by calling IDDestroyTable), then calling IDTableCopy.


4.      Make changes
to your unread list (not your "point of divergence") using the IDxxx
routines, such as IDInsert and IDDelete.  Call NSFDbSetUnreadNoteTable to push
your unread list changes back to the database.


5.      After
calling NSFDbSetUnreadNoteTable, if you will be doing additional work with the
unread list, you should always calling NSFDbUpdateUnread to update the unread
list, calling IDDestroyTable to delete the old "point of divergence",
then calling IDTableCopy to recreate the updated "point of
divergence".   


 


You can use
the unread note table functions to update a note, but leave it in the same
read/unread state as it was originally.  The steps are: 


*       
First open the database and call NSFDbGetUnreadNoteTable to get
the original unread note table (hTable), call NSFDbUpdateUnread to update the
list, and call IDTableCopy to create a copy of the original unread table
(hOriginalTable).  


*       
Check to see if the note you want to change is in the unread note
table (hTable).  


*       
Open the note, make the changes, call NSFNoteUpdate and then call
NSFNoteClose to save the changes. 


*       
Call  NSFDbUpdateUnread to update the unread table (hTable).  Now,
the unread table contains the changed note.


*       
If the note you just changed was originally not in the unread note
table (hTable), use the following steps to take it out of the unread list. 


*       
Drop the old copy of the original unread table using
IDDestroyTable, then calling IDTableCopy to re-establish a new "point of
divergent ", i.e. a new copy of the original unread table
(hOriginalTable).  


*       
Call IDDelete to delete this note id from the unread table
(hTable).  


*       
Lastly, feed both the unread table and the original unread table
to NSFDbSetUnreadNoteTable to update the unread table in the database.


*       
After calling NSFDbSetUnreadNoteTable, if you're going to continue
to use the unread list, it's a good idea to:


*       
call NSFDbUpdateUnread.


*       
call IDDestroyTable to destroy your "old" "point of
divergent".


*       
call IDTableCopy to re-establish your new "point of
divergent".  

  

  




No
coordination is done between different processes accessing the same unread
list.  If another user views the uread list while an application is updating
the list, the changes may not be visible.  If multiple sessions attempt to set
the unread note list, the changes are not merged.  Instead, only changes from
the last session to update the list will be preserved.


 


      In
Domino and Notes, unread marks for each user are stored in the client
desktop.dsk file and in the database.  When a user closes a database (either
through the Notes user interface or through an API program), the unread marks
in the desktop.dsk file and in the database are synchronized so that they
match.  Unread marks are not replicated when a database is replicated. 
Instead, when a user opens a replica of a database, the unread marks from the
desktop.dsk file propagates to the replica database.  NSFDbSetUnreadNoteTable
only accesses the unread marks stored in the database and does not attempt to
synchronize with the unread marks in desktop.dsk.  


 


**Parameters :**



Input :  

hDB  -  Handle of the database.  

  

UserName  -  Pointer to the fully distinguished user name LMBCS string.  

  

UserNameLength  -  Number of bytes in the user name string.  

  

fFlushToDisk  -  FALSE:  Allow Domino or Notes to buffer the updates in memory.  

TRUE:  Write updates to disk immediately.  

  

hOriginalUnreadList  -  Handle of a copy of the unmodified unread note ID
table.  This copy is required to merge any updates.  

  

hUnreadUnreadList  -  Handle to the modified unread note ID table.  

  




Output :  

(routine)  -  Return status from this call:  

  

NOERROR - Success  

ERR\_NOT\_LOCAL - Attempted to get an unread note table from a remote database.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  




 **Sample Usage :**


DBHANDLE   hDb;  

STATUS     status;  

DHANDLE    hTable;  

DHANDLE    hOriginalTable;  

char               UserName [MAXUSERNAME + 1];  

  

    /\* Get the current user name \*/  

status = SECKFMGetUserName (UserName);  

  

    /\* Get the unread list \*/  

status = NSFDbGetUnreadNoteTable (  

    hDb,  

    UserName,  

    strlen (UserName),  

    TRUE,                  /\* Create list if it's not already there \*/  

    &hTable);  

  

    /\* Bring table up to date \*/  

status = NSFDbUpdateUnread (hDb, hTable);  

  




      /\* Notes requires
original unread table to merge changes \*/  

status = IDTableCopy (hTable, &hOriginalTable);


   if ( status !=
NOERROR ) 


   {


      
IDDestroyTable(hTable);


       return(status);


   }  

  

    /\* Make some changes \*/  

status = IDInsert (hTable, 0x2102L, NULL);  

status = IDDelete (hTable, 0x20FEL, NULL);  

  

    /\* Merge changes \*/  

status = NSFDbSetUnreadNoteTable (  

    hDb,  

    UserName,  

    strlen (UserName),  

    FALSE,         /\* Don't force the write to disk \*/  

    hOriginalTable,  

    hTable);  

  

status = IDDestroyTable (hOriginalTable);


 


   status =
IDDestroyTable (hTable);


 **See Also :**


**[NSFDbUpdateUnread](NSFDbUpdateUnread.md)**


**[NSFDbGetUnreadNoteTable](NSFDbGetUnreadNoteTable.md)**


**[DNCanonicalize](DNCanonicalize.md)**



----------------------------------------------------------------------------------------------------------


 





