##### Function : Note
##### NSFNoteClose - Closes an open note.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteClose(

	NOTEHANDLE  note_handle);
```
**Description :**

This function deallocates the memory associated with an open note.  Closing a 
note does not write the contents of the note to disk. That function is 
performed by NSFNoteUpdate.

**Parameters :**
Input :
note_handle  -  The handle of the note that you want to close.

Output :
(routine)  -  Always returns NOERROR



**Sample Usage :**
```

    cleanup_state -= CLOSE_NOTE1;
    NSFNoteClose(note1_handle);

```
**See Also :**
[NSFNoteCreate](/domino-c-api-docs/reference/Func/NSFNoteCreate)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
---
