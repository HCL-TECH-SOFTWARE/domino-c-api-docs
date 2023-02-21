##### Function : Note
##### NSFNoteOpenSoftDelete - Opens a soft deleted note from a database.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteOpenSoftDelete(

	DBHANDLE  hDB,
	NOTEID  NoteID,
	DWORD  Reserved,
	NOTEHANDLE *rethNote);
```
**Description :**

This function reads a "soft deleted" note into memory and returns a handle to 
the in-memory copy.  Its input is a database handle and a note ID within that 
database.  

Use NSFNoteClose to close the note handle and deallocate the memory associated 
with it.

	Use NSFNoteUpdate or NSFNoteUpdateExtended to restore this "soft 
deleted" note.

**Parameters :**
Input :
hDB  -  The handle of the database that contains the note.

NoteID  -  The ID of the "soft deleted" note to open

Reserved  -  Not used.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully opened.
ERR_DIRECTORY - This function is inappropriate for directories.
ERR_NOACCESS - You are not authorized to perform that operation.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


rethNote  -  The address of a NOTEHANDLE in which the handle of the opened "soft deleted" note is returned.


**See Also :**
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
[NSFNoteUpdateExtended](/domino-c-api-docs/reference/Func/NSFNoteUpdateExtended)
---
