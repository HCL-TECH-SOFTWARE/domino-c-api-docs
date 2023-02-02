##### Function : Note
##### NSFNoteOpenWithLock - Lock a note.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteOpenWithLock(**

	DBHANDLE  hDB,
	NOTEID  NoteID,
	DWORD  LockFlags,
	DWORD  OpenFlags,
	char *pLockers,
	DHANDLE *rethLockers,
	DWORD *retLength,
	NOTEHANDLE far *rethNote);
**Description :**
This function will open a note, much like the function NSFNoteOpenExt, but it 
will also add an "authors" field to a note which contains a list of "writers" 
who will be able to update the note.  Any user will be able to open the note, 
but only the members contained in the "authors" field are allowed to update the 
note.

This function will only succeed if the database option "Allow document locking" 
is set.  Please refer to the Domino documentation for a full description of 
document locking.
**Parameters :**
Input :
hDB  -  The handle of the open database that contains the note.

NoteID  -  The ID of the note that you want to open and lock.

LockFlags  -  Flags to control how a note is locked.  See NOTE_LOCK_xxx.

OpenFlags  -  Flags that control the manner in which the note is opened. This, in turn, controls what information about the note is available to you and how it is structured. The flags are defined in OPEN_xxx (note) and may be or'ed together to combine functionality.

pLockers  -  A pointer to a null-terminated character string containing the name or names to be added to the authors field.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Success.

ERR_NOTE_LOCKED - The note is already locked.  You can determine who locked the note by setting the NOTE_LOCK_STATUS flag  and using the rethLockers parameter.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, etc.).  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethLockers  -  If the note is already locked and you specify the NOTE_LOCK_STATUS flag, this is the handle to the "lockers".

retLength  -  Length of the string associated with rethLockers.

rethNote  -  The address of a NOTEHANDLE in which the handle of the opened note is returned.

**See Also :**
[NSFDbNoteLock](D:/md_files/NSFDbNoteLock.md)
[NSFDbNoteUnlock](D:/md_files/NSFDbNoteUnlock.md)
[NSFNoteClose](D:/md_files/NSFNoteClose.md)
[NSFNoteOpenExt](D:/md_files/NSFNoteOpenExt.md)
[NSFNoteUpdate](D:/md_files/NSFNoteUpdate.md)
[OPEN_xxx (note)](D:/md_files/OPEN_xxx (note).md)
---
