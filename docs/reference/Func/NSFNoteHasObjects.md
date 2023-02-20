##### Function : Note
##### NSFNoteHasObjects - Returns TRUE if note contains any object items. FALSE otherwise.
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFNoteHasObjects(

	NOTEHANDLE  hNote,
	BLOCKID far *bhFirstObjectItem);
```
**Description :**

This returns TRUE if the specified note contains any object items, FALSE 
otherwise. 

Object items are items of type TYPE_OBJECT. Domino and Notes use objects to 
store data that is not rendered on the screen by the Notes editor. Examples 
include file attachments ($FILE fields), help indexes, and macro left-to-do 
lists ($LeftToDo fields).

The BLOCKID value obtained using this function refers to memory within a note.  
This memory is managed by Domino and Notes, and should not be freed by the 
application.

**Parameters :**
Input :
hNote  -  Handle to the open note.

Output :
(routine)  -  TRUE if note contains any object items.


bhFirstObjectItem  -  Receives the BLOCKID of the object item. Note: this variable receives the item BLOCKID, not the value BLOCKID. The item block ID is the same as what is received by item_blockid in NSFItemInfo, not value_blockid.


**See Also :**
[NSFItemAppendObject](/reference/Func/NSFItemAppendObject)
[NSFNoteAttachFile](/reference/Func/NSFNoteAttachFile)
---
