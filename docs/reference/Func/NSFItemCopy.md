##### Function : Item (Field)
##### NSFItemCopy - Copies an item from one note to another by BLOCKID.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemCopy(

	NOTEHANDLE  note_handle,
	BLOCKID  item_blockid);
```
**Description :**

Copies an item identified by its BLOCKID from one in-memory copy of a note to 
another.  

 Note:  If the item copied is of type TYPE_COMPOSITE (a rich text field) and 
contains a doclink, the doclink is not preserved in the new copy of the item.  
The doclink symbol will be displayed, but Notes will not be able to locate the 
document when the user attempts to activate the doclink. 

Also Note:  If the item copied already exists in the destination note, the 
item's value in the destination note will not be replaced by the value of the 
item in the source note.  Rather, the item will retain its original value, and 
the new copy of the item will be appended to the destination note.  Therefore, 
the destination note will have two items with the same name, and only the 
original one will be visible. If the intent is to replace the value of an item 
in the destination note with the value of the item in the source note, be sure 
that the item is first deleted in the destination note before calling this 
function.

**Parameters :**
Input :
note_handle  -  Handle of note to which item is to be copied.

item_blockid  -  The BLOCKID for  the item you wish to copy.
  Note:  This is the BLOCKID of the item's header information ( the item_block_id returned by NSFItemInfo() ), not the BLOCKID of the actual item itself ( the value_block_id returned by NSFItemInfo() ).

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - upon successfully copying the item.

ERR_xxx - STATUS returned from a lower level Notes function called in the action routine and passed back.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.



**See Also :**
[NSFItemScan](/domino-c-api-docs/reference/Func/NSFItemScan)
[NSFItemInfo](/domino-c-api-docs/reference/Func/NSFItemInfo)
[NSFItemInfoNext](/domino-c-api-docs/reference/Func/NSFItemInfoNext)
[NSFItemDelete](/domino-c-api-docs/reference/Func/NSFItemDelete)
---
