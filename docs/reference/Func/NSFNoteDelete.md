##### Function : Note
##### NSFNoteDelete - Deletes a note from a database.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteDelete(

	DBHANDLE  db_handle,
	NOTEID  note_id,
	WORD  update_flags);
```
**Description :**

This function takes a database handle, note ID, and a WORD of UPDATE_xxx 
flag(s) as input and deletes the specified note from the specified database. 
This function only supports the set of 16-bit WORD options described in the 
entry UPDATE_xxx;  to use the extended 32-bit DWORD options, use the function 
NSFNoteDeleteExtended().

It deletes the specified note by updating it with a nil body, and marking the 
note as a deletion stub.  The deletion stub identifies the deleted note to 
other replica copies of the database.  This allows the replicator to delete 
copies of the note from replica databases. 

The deleted note may be of any NOTE_CLASS_xxx.  The active user ID must have 
sufficient user access in the databases's Access Control List (ACL) to carry 
out a deletion on the note or the function will return an error code.

**Parameters :**
Input :
db_handle  -  The handle of the database that contains the note.

note_id  -  The ID of the note that you want to delete.

update_flags  -  Flags that control the manner in which the database is updated.  See UPDATE_xxx for further information.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The note was successfully deleted.
ERR_DIRECTORY - This function is inappropriate for directories.
ERR_NOACCESS - You are not authorized to perform that operation.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.



**Sample Usage :**
```

if (error = NSFNoteDelete (db_handle, note_id, 0))
{ 
    NSFDbClose (db_handle);
    return (ERR(error));
}
```
**See Also :**
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
[UPDATE_xxx](/domino-c-api-docs/reference/Symb/UPDATE_xxx)
---
