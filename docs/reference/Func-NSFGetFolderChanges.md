##### Function : Folders
##### NSFGetFolderChanges - Get the ID Tables of notes added to or removed from a folder.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFGetFolderChanges(**

	DBHANDLE  hViewDB,
	DBHANDLE  hDataDB,
	NOTEID  ViewNoteID,
	TIMEDATE *Since,
	DWORD  Flags,
	DHANDLE *AddedNoteTable,
	DHANDLE *RemovedNoteTable);
**Description :**
This function gets the Note IDs of notes added to or removed, not deleted, from 
a folder and returns the handles of the respective ID Tables.  This function 
works on folders only and is not supported for remote databases.
**Parameters :**
Input :
hViewDB  -  The handle of the database that contains the folder.

hDataDB  -  The handle of the database that contains the data notes.  This must reference the same database as hViewDB.

ViewNoteID  -  The ID of the folder note in the database. Use NIFFindView to obtain the note ID of a folder note given its name.

Since  -  A pointer to a TIMEDATE structure containing the starting date used to determine which notes have been added or removed, not deleted, from the folder and added to the ID Tables returned by this function.  Passing a cleared TIMEDATE structure (TimeDateClear), will return all changes since the start of the database.

Flags  -  Reserved, must be zero.

Output :
(routine)  -  (routine)  -  Return status from this call:

NOERROR - Success

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


AddedNoteTable  -  Address to the handle of the ID Table containing the net amount of notes added to the folder.

RemovedNoteTable  -  Address to the handle of the ID Table containing the net amount of notes removed, not deleted, from the folder.

**See Also :**
[NSFFolderGetIDTable](D:/md_files/NSFFolderGetIDTable.md)
[TimeDateClear](D:/md_files/TimeDateClear.md)
---
