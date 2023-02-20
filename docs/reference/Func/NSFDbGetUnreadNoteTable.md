##### Function : Unread Notes
##### NSFDbGetUnreadNoteTable - Create an ID Table of unread notes
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetUnreadNoteTable(

	DBHANDLE  hDB,
	char far *UserName,
	WORD  UserNameLength,
	BOOL  fCreateIfNotAvailable,
	DHANDLE far *rethUnreadList);
```
**Description :**

An ID Table is created containing the list of unread notes in the open database 
for the specified user, and the handle of that ID Table is returned.  Prior to 
Release 4.5 of Notes, this function will only work with local databases.  If 
both the workstation and the server have Release 4.5 or later installed, this 
function will also work with remote databases.  The user name must be the 
complete user name, as it would be retrieved from the user's ID file.  In 
particular, if the name is hierarchical, the user name string must be the fully 
distinguished hierarchical user name.  This form of the name may be obtained by 
calling DNCanonicalize().

The argument fCreateIfNotAvailable controls what action is to be performed if 
there is no list of unread notes for the specified user in the database.  If no 
list is found and this flag is set to FALSE, the handle returned will be NULL;  
if this flag is set to TRUE, the list of unread notes will be created and all 
notes in the database will be added to the list.

No coordination is performed between different users of the same database.  If 
an application obtains a list of unread notes while another user is modifying 
the list, the changes made may not be visible to the application.

	Unread marks for each user are stored in the client desktop.dsk file 
and in the database.  When a user closes a database (either through the Notes 
user interface or through an API program), the unread marks in the desktop.dsk 
file and in the database are synchronized so that they match.  Unread marks are 
not replicated when a database is replicated.  Instead, when a user opens a 
replica of a database, the unread marks from the desktop.dsk file propagates to 
the replica database.  NSFDbGetUnreadNoteTable only accesses the unread marks 
stored in the database and does not attempt to synchronize with the unread 
marks in desktop.dsk.  

**Parameters :**
Input :
hDB  -  Handle of the database.

UserName  -  Pointer to the fully distinguished user name LMBCS string.

UserNameLength  -  Number of bytes in the user name string.

fCreateIfNotAvailable  -  TRUE: If the unread list for this user cannot be found on disk, return all note IDs.
FALSE:  If the list cannot be found, return an ID Table handle of NULL

Output :
(routine)  -  Return status from this call:

NOERROR - Success
ERR_NOT_LOCAL - Attempted to get an unread note table from a remote database.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethUnreadList  -  Address where the handle for the ID Table will be stored.  The application must free this storage using IDDestroyTable().


**Sample Usage :**
```
DBHANDLE  hDb;
STATUS  status;
DHANDLE  hTable;
DHANDLE  hOriginalTable;
char    UserName [MAXUSERNAME + 1];

/* Get the current user name */
status = SECKFMGetUserName (UserName);

/* Get the unread list */
status = NSFDbGetUnreadNoteTable (
  hDb,
  UserName,
  strlen (UserName),
  TRUE,      /* Create list if it's not already there */
  &hTable);

/* Notes requires original unread table to merge changes */
status = IDTableCopy (hTable, &hOriginalTable);

/* Bring table up to date */
status = NSFDbUpdateUnread (hDb, hTable);

/* Make some changes */
status = IDInsert (hTable, 0x2102L, NULL);
status = IDDelete (hTable, 0x20FEL, NULL);

/* Merge changes */
status = NSFDbSetUnreadNoteTable (
  hDb,
  UserName,
  strlen (UserName),
  FALSE,    /* Don't force the write to disk */
  hOriginalTable,
  hTable);

status = IDDestroyTable (hOriginalTable);
```
**See Also :**
[NSFDbUpdateUnread](/reference/Func/NSFDbUpdateUnread)
[NSFDbSetUnreadNoteTable](/reference/Func/NSFDbSetUnreadNoteTable)
[DNCanonicalize](/reference/Func/DNCanonicalize)
---
