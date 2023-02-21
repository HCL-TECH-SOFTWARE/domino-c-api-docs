##### Function : Item (Field)
##### NSFItemDelete - Deletes an item from a note by name.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemDelete(

	NOTEHANDLE  note_handle,
	const char far *item_name,
	WORD  name_len);
```
**Description :**

Deletes a named item from the in-memory copy of a note.

**Parameters :**
Input :
note_handle  -  Handle of note from which item is to be deleted.

item_name  -  The name of the item in the note. This name is equivalent to the field name when you design a form using the screen interface. 

name_len  -  The length of item_name.

Output :
(routine)  -  Return status from this call.  A successful call returns NOERROR.



**See Also :**
[NSFItemAppend](/domino-c-api-docs/reference/Func/NSFItemAppend)
[NSFItemAppendByBLOCKID](/domino-c-api-docs/reference/Func/NSFItemAppendByBLOCKID)
[NSFItemDeleteByBLOCKID](/domino-c-api-docs/reference/Func/NSFItemDeleteByBLOCKID)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
---
