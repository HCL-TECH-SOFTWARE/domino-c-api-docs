##### Function : Note
##### NSFNoteCreate - Creates a new in-memory note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteCreate(

	DBHANDLE  db_handle,
	NOTEHANDLE far *note_handle);
```
**Description :**

This function creates a new note in memory. The note is empty after creation 
and is not yet stored in the on-disk database. You may use NSFItemAppend to add 
fields to the note, and NSFNoteUpdate to write the note to disk.  Use 
NSFNoteClose to close the note handle and deallocate the memory associated with 
it.


**Parameters :**
Input :
db_handle  -  The handle of the database in which you want to create a new note.

Output :
(routine)  -  Return status from this call. Possible values:
NOERROR - Note successfully created.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


note_handle  -  The address of a NOTEHANDLE in which handle of the new empty note is returned.


**Sample Usage :**
```

   /* Create a Note in the specified database. */
   if (error_status = NSFNoteCreate(db_handle, &note1_handle))
       goto Exit;
   else
       cleanup_state += CLOSE_NOTE1;

```
**See Also :**
[NSFItemAppend](/domino-c-api-docs/reference/Func/NSFItemAppend)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
---
