##### Function : Note
##### NSFNoteHardDelete - Hard deletes a soft deleted note from a database.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteHardDelete(

	DBHANDLE  hDB,
	NOTEID  NoteID,
	DWORD  Reserved);
```
**Description :**

This function takes a database handle and note ID as input and permanently 
deletes the specified "soft deleted" note from the specified database. 

The deleted note may be of any NOTE_CLASS_xxx.  The active user ID must have 
sufficient user access in the databases's Access Control List (ACL) to carry 
out a deletion on the note or the function will return an error code.

**Parameters :**
Input :
hDB  -  The handle of the database that contains the note.

NoteID  -  The ID of the note that you want to delete.

Reserved  -  Not used.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully deleted.
ERR_DIRECTORY - This function is inappropriate for directories.
ERR_NOACCESS - You are not authorized to perform that operation.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.



**See Also :**
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpenSoftDelete](/reference/Func/NSFNoteOpenSoftDelete)
---
