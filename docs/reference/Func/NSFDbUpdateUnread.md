##### Function : Unread Notes
##### NSFDbUpdateUnread - Update the unread note table.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbUpdateUnread(

	DBHANDLE  hDataDB,
	DHANDLE  hUnreadList);
```
**Description :**

The unread note table in memory is updated to reflect any changes in the list 
of unread notes in the database since the last call to 
NSFDbGetUnreadNoteTable() or NSFDbUpdateUnread().  

	In Domino and Notes, unread marks for each user are stored in the 
client desktop.dsk file and in the database.  When a user closes a database 
(either through the Notes user interface or through an API program), the unread 
marks in the desktop.dsk file and in the database are synchronized so that they 
match.  Unread marks are not replicated when a database is replicated.  
Instead, when a user opens a replica of a database, the unread marks from the 
desktop.dsk file propagates to the replica database.  NSFDbUpdateUnread only 
accesses the unread marks stored in the database and does not attempt to 
synchronize with the unread marks in desktop.dsk.  

**Parameters :**
Input :
hDataDB  -  Handle of the database.

hUnreadList  -  Handle of the memory block containing the unread note table.

Output :
(routine)  -  Return status from this call:

NOERROR - Success
ERR_NOT_LOCAL - Attempted to get an unread note table from a remote database.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


hUnreadList  -  The handle is not modified, but the ID table is updated to reflect any changes to the unread note list in the database.


**Sample Usage :**
```
DBHANDLE hDb;
STATUS status;
DHANDLE hTable;
DHANDLE hOriginalTable;
char     UserName [MAXUSERNAME + 1];

 /* Get the current user name */
status = SECKFMGetUserName (UserName);

 /* Get the unread list */
status = NSFDbGetUnreadNoteTable (
 hDb,
 UserName,
 strlen (UserName),
 TRUE,   /* Create list if it's not already there */
 &hTable);

 /* Bring table up to date */
status = NSFDbUpdateUnread (hDb, hTable);

      /* Notes requires original unread table to merge changes */
status = IDTableCopy (hTable, &hOriginalTable);
   if ( status != NOERROR ) 
   {
       IDDestroyTable(hTable);
       return(status);
   }

 /* Make some changes */
status = IDInsert (hTable, 0x2102L, NULL);
status = IDDelete (hTable, 0x20FEL, NULL);

 /* Merge changes */
status = NSFDbSetUnreadNoteTable (
 hDb,
 UserName,
 strlen (UserName),
 FALSE,  /* Don't force the write to disk */
 hOriginalTable,
 hTable);

status = IDDestroyTable (hOriginalTable);

   status = IDDestroyTable (hTable);
```
**See Also :**
[NSFDbGetUnreadNoteTable](/domino-c-api-docs/reference/Func/NSFDbGetUnreadNoteTable)
[NSFDbSetUnreadNoteTable](/domino-c-api-docs/reference/Func/NSFDbSetUnreadNoteTable)
---
