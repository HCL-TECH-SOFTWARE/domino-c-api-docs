##### Function : Note
##### NSFNoteOpenExt - Opens a note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteOpenExt(

	DBHANDLE  hDB,
	NOTEID  NoteID,
	DWORD  flags,
	NOTEHANDLE *rethNote);
```
**Description :**

This function reads a note into memory and returns a handle to the in-memory 
copy.  Its input is a database handle and a note ID within that database.  It 
is similar to NSFNoteOpen with additional options for the flags parameter.  
This function allows using extended 32-bit DWORD update options, as described 
in the entry OPEN_xxx.

If the note is marked as unread, by default this function does not change the 
unread mark.  You can use the OPEN_MARK_READ flag to change an unread mark to 
read for remote databases.

Use NSFNoteClose to close the note handle and deallocate the memory associated 
with it.

**Parameters :**
Input :
hDB  -  The handle of the open database that contains the note.

NoteID  -  The ID of the note that you want to open.

flags  -  Flags that control the manner in which the note is opened. This, in turn, controls what information about the note is available to you and how it is structured. The flags are defined in OPEN_xxx (note) and may be or'ed together to combine functionality.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_DIRECTORY
ERR_NOACCESS
ERR_INVALID_ITEMUNK


rethNote  -  The address of a NOTEHANDLE in which the handle of the opened note is returned.


**Sample Usage :**
```

   /* Reopen the Note and examine its contents */
   if (error_status = NSFNoteOpenExt(db_handle, note1_id,
                                  0, &note1_handle))
       goto Exit;
   else
       cleanup_state += CLOSE_NOTE1;

```
**See Also :**
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteCreate](/domino-c-api-docs/reference/Func/NSFNoteCreate)
[NSFNoteOpenByUNID](/domino-c-api-docs/reference/Func/NSFNoteOpenByUNID)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
[OPEN_xxx (note)](/domino-c-api-docs/reference/Symb/OPEN_xxx (note))
---
