##### Function : Folders
##### NSFFolderGetIDTable - Get the ID Table of notes in a folder.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFFolderGetIDTable(

	DHANDLE  hViewDB,
	DHANDLE  hDataDB,
	NOTEID  ViewNoteID,
	DWORD  Flags,
	DHANDLE *hTable);
```
**Description :**

This function gets the Note IDs of notes in a folder and returns the handle of 
the ID Table. 

**Parameters :**
Input :
hViewDB  -  The handle of the database that contains the view or folder.

hDataDB  -  The handle of the database that contains the data notes.  For folders this must reference the same database as hViewDB.

ViewNoteID  -  The ID of the view or folder note in the database. Use NIFFindView to obtain the note ID of a view or folder note given its name.


Flags  -  DWORD containing DB_GETIDTABLE_xxx flags

Output :
(routine)  -  Return status from this call:

NOERROR - Success
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


hTable  -  Address where the handle for the ID Table will be stored. 


**See Also :**
[DB_GETIDTABLE_xxx](/domino-c-api-docs/reference/Symb/DB_GETIDTABLE_xxx)
---
