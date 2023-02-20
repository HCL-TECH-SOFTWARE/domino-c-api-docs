##### Function : Item (Field)
##### NSFItemDeleteByBLOCKID - Deletes an item from a note by BLOCKID.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemDeleteByBLOCKID(

	NOTEHANDLE  note_handle,
	BLOCKID  item_blockid);
```
**Description :**

Deletes an item specified by its BLOCKID from the in-memory copy of a note, and 
deallocates the storage associated with the item.

Use NSFItemDeleteByBLOCKID to delete and item from a Note if you do not have 
the item name. You may obtain an item BLOCKID without the item name by 
specifying NULL as the item_name input argument to NSFItemInfo() or 
NSFItemInfoNext().  NSFItemDeleteByBLOCKID() may also be useful if there are 
multiple items that have the same name in the note, and you want to delete a 
particular one.

Normally, if you know the name of the item, use NSFItemDelete to delete the 
item from the note.

**Parameters :**
Input :
note_handle  -  Handle of note from which item is to be deleted.

item_blockid  -  The BLOCKID of the item (NOT the BLOCKID of the item's value) to be removed from the note and deallocated.

Output :
(routine)  -  Always returns NOERROR.



**Sample Usage :**
```

NOTEHANDLE   hRespNote;
BLOCKID     bhThisBodyItem;
WORD        wBodyType;
BLOCKID     bhBodyValue;
DWORD       dwBodyValueLength;

/* steps missing ... */

if (status = NSFItemInfo(   hRespNote,
                        szBodyFieldName,
                        lstrlen(szBodyFieldName),
                        &bhThisBodyItem,
                        &wBodyType,
                        &bhBodyValue,
                        &dwBodyValueLength ))
{
    /* Unable to get body of response document */
    goto Exit1;
}

if (status = NSFItemDeleteByBLOCKID( hRespNote, bhThisBodyItem ))
{
    /* Unable to delete old body from response document*/
    goto Exit3;
}

```
**See Also :**
[NSFItemAppend](/reference/Func/NSFItemAppend)
[NSFItemAppendByBLOCKID](/reference/Func/NSFItemAppendByBLOCKID)
[NSFItemDelete](/reference/Func/NSFItemDelete)
[NSFItemInfo](/reference/Func/NSFItemInfo)
[NSFItemInfoNext](/reference/Func/NSFItemInfoNext)
---
