##### Function : Note
##### NSFDbNoteUnlock - Unlock a note
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFDbNoteUnlock(

	DBHANDLE  hDB,
	NOTEID  NoteID,
	DWORD  Flags);
```
**Description :**

This function removes the lock on a note.  Only the members contained in the 
"writers" list are allowed to remove a lock, with the exception of person(s) 
designated as capable of removing locks.  

Please refer to the Domino documentation for a full description of document 
locking.

**Parameters :**
Input :
hDB  -  The handle of the open database that contains the note to be unlocked.

NoteID  -  The ID of the note that you want to unlock.

Flags  -  Flags to control how a note is locked.  See NOTE_LOCK_xxx.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Success.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, etc.).  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**See Also :**
[NSFDbNoteLock](/domino-c-api-docs/reference/Func/NSFDbNoteLock)
---
