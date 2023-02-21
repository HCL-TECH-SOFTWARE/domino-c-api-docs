##### Function : Item (Field)
##### NSFItemAppendByBLOCKID - Adds an item value to a note by BLOCKID.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemAppendByBLOCKID(

	NOTEHANDLE  note_handle,
	WORD  item_flags,
	const char far *item_name,
	WORD  name_len,
	BLOCKID  value_bid,
	DWORD  value_len,
	BLOCKID far *item_bid_ptr);
```
**Description :**

This function adds an item (field) to the in-memory copy of a note using the 
BLOCKID of the item value. Call NSFNoteUpdate to write the modified note to 
disk.

Unlike NSFItemAppend, NSFItemAppendByBLOCKID does not copy the memory 
associated with the value BLOCKID. Instead, it transfers ownership of memory to 
the note. Unlock the memory associated with the BLOCKID but do not free it. 
NSFNoteClose will free the memory. Warning: to avoid associating the same 
memory with more than one note, do not use a BLOCKID obtained by calling 
NSFItemInfo with the handle to a different note.

Use this function to append an item to a note if you happen to have the item 
data in a Domino memory block. Otherwise, it is generally more convenient to 
use NSFItemAppend.

API programs on a non-Intel architecure machines must convert the item value to 
Domino Canonical Format before calling NSFItemAppend if value_bid is one of the 
following: 

    TYPE_COMPOSITE
    TYPE_COLLATION
    TYPE_OBJECT
    TYPE_VIEW_FORMAT
    TYPE_ICON
    TYPE_SIGNATURE
    TYPE_SEAL
    TYPE_SEALDATA
    TYPE_SEAL_LIST
    TYPE_WORKSHEET_DATA
    TYPE_USERDATA

Use ODSWriteMemory() to convert item data from host specific format to Domino 
canonical format before calling NSFItemAppendByBLOCKID.

Note that the data type word - - the first word in the memory object specified 
by value_bid - - is in Host specific format, not Domino Canonical Format.

**Parameters :**
Input :
note_handle  -  The handle to the note that will receive this item.

item_flags  -   The flags that define the characteristics of this item. These flags are defined in ITEM_xxx and may be bitwise or'ed together for combined functionality.

item_name  -  Text buffer containing the name of the item as it will appear in the note. This name is equivalent to the field name when you design a form using the screen interface.

name_len  -  The length of item_name.

value_bid  -  The BLOCKID of a Domino memory block that contains the item's datatype word followed by the item value.  The data type word is always in host format. The item value data following the data type word must be in Domino canonical format only if the data type is one of  TYPE_COMPOSITE, TYPE_COLLATION, TYPE_OBJECT, TYPE_VIEW_FORMAT, TYPE_ICON, TYPE_SIGNATURE, TYPE_SEAL, TYPE_SEALDATA, TYPE_SEAL_LIST, TYPE_WORKSHEET_DATA, or TYPE_USERDATA.

value_len  -  Length of the memory object in BYTES, including the Domino data type WORD.

Output :
(routine)  -  Return status from this call.  

NOERROR - Successfully appended Item to the note.

ERR_xxx - Errors returned by lower level functions. Use OSLoadString to convert the status to a message string and display the string to the user.


item_bid_ptr  -  The specified location gets the item BLOCKID of the newly appended item (field).  You may need the item BLOCKID in API routines such as NSFItemInfoNext and NSFItemDeleteByBLOCKID. Specify NULL if you do not wish this value to be returned.  This block is part of the memory allocated for the note, and is managed by Domino and Notes;  the application should not free this block.


**Sample Usage :**
```

   /* Fabricate an Item and append it to Note2 by BLOCKID  */

   if (error_status = OSMemAlloc(0, LINEOTEXT, &fab_value_bid.pool))
       goto Exit;
   else
       cleanup_state += FREE_BIDMEM;

   fab_value_bid.block = NULLBLOCK;
   value_ptr = OSLockBlock(char, fab_value_bid);
   cleanup_state += UNLOCK_BIDMEM;

   *(WORD *) value_ptr = TYPE_TEXT;
   value_ptr += sizeof(WORD);
   strcpy(value_ptr, "What a Country!");

   value_len = strlen(value_ptr) + sizeof(WORD);
   item_flags = ITEM_SUMMARY;

   OSUnlockBlock(fab_value_bid);
   cleanup_state -= UNLOCK_BIDMEM;

   if (error_status=NSFItemAppendByBLOCKID(note2_handle, item_flags,
                               TEXT_ITEM, strlen(TEXT_ITEM),
                               fab_value_bid, value_len, NULL))
       goto Exit;

```
**See Also :**
[ITEM_xxx](/domino-c-api-docs/reference/Symb/ITEM_xxx)
[NSFItemInfo](/domino-c-api-docs/reference/Func/NSFItemInfo)
[NSFItemQuery](/domino-c-api-docs/reference/Func/NSFItemQuery)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
[OSLockBlock](/domino-c-api-docs/reference/Func/OSLockBlock)
[OSMemAlloc](/domino-c-api-docs/reference/Func/OSMemAlloc)
[OSUnlockBlock](/domino-c-api-docs/reference/Func/OSUnlockBlock)
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
---
