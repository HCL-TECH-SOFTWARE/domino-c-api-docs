##### Function : Note
##### NSFNoteGetInfo - Gets specified value from in-memory note header.
---
```
#include <nsfnote.h>
void LNPUBLIC NSFNoteGetInfo(

	NOTEHANDLE  note_handle,
	WORD  note_member,
	void far *value_ptr);
```
**Description :**

This function gets a specified value from an in-memory note header.  It takes a 
handle to an open note,  a note member ID identifying the information you wish 
to obtain, and the address of a variable where the requested data will be 
returned. 

**Parameters :**
Input :
note_handle  -  The handle of an open note.

note_member  -  A WORD containing the note member ID (see _NOTE_xxx) for the note header value you wish to get.

Output :
(routine)  -  None.


value_ptr  -  The address of an existing variable or Domino memory object in which the requested note header data will be returned.


**Sample Usage :**
```

   /* Since NID only exists if Note exists on disk, Update, Get,  */   
   /* and store the resulting NID                                 */
   if (error_status = NSFNoteUpdate(note1_handle, UPDATE_FORCE))
       goto Exit;
   NSFNoteGetInfo(note1_handle, _NOTE_ID, &note1_id);

```
**See Also :**
[NSFDbGenerateOID](/reference/Func/NSFDbGenerateOID)
[NSFNoteClose](/reference/Func/NSFNoteClose)
[NSFNoteOpen](/reference/Func/NSFNoteOpen)
[NSFNoteSetInfo](/reference/Func/NSFNoteSetInfo)
[NSFNoteUpdate](/reference/Func/NSFNoteUpdate)
[_NOTE_xxx](/reference/Symb/_NOTE_xxx)
---
