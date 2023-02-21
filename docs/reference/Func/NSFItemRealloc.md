##### Function : Item (Field)
##### NSFItemRealloc - Reallocate memory associated with an item value.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFItemRealloc(

	BLOCKID  item_blockid,
	BLOCKID far *value_blockid_ptr,
	DWORD  value_len);
```
**Description :**

This function reallocates the memory block associated with an item's value to 
the amount requested. Use this function to change the amount of memory 
associated with an item's value. If possible, this function resizes the memory 
block that contains the value, otherwise the function allocates a new block and 
copies the existing value there, and deletes the old block. Since the memory 
block might move, you should unlock it if necesssary (using OSUnlockBlock) 
before calling this function.

This function stores the new value length in the item header and returns the 
BLOCKID of the new block of memory.  The new block will contain the existing 
value of the item, up to the length of the block.  On successful return,  the 
caller should immediately write the new item value to the memory identified by 
the returned BLOCKID.

If this function returns successfully and a subsequent error prevents you from 
writing the new item value to the new memory area, either delete the item from 
the note or do not update the note to disk. Otherwise the value will not have a 
consistent length, and Domino or Notes may detect the item as damaged.

**Parameters :**
Input :
item_blockid  -  BLOCKID of Item whose size you wish to change.

value_blockid_ptr  -  A pointer to the value's BLOCKID.  The reallocation will maintain the current contents of the item's value. 

value_len  -  A DWORD containing the new length of the Item's value required.  This length must include the  data type word.  If it does not, subsequent manipulation of the value's BLOCKID will overwrite other areas of memory.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - upon successfully copying the item.

ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


value_blockid_ptr  -   If the resizing requires any change in location within memory managed by Domino and Notes,  the value's BLOCKID will be modified accordingly and returned.


**Sample Usage :**
```
	// get the field

 if ( err = NSFItemInfo(hNote,
     szItemName,
     lstrlen(szItemName),
     &item_block,
     &item_type,
     &value_block,
     &value_len))
    goto done;

 wsprintf(szBuff, "Got item %s, type 0x%04x, len 0x%08lx", szItemName, 
item_type,                        
                         value_len);


 // Realloc to a slightly shorter length

 newlen = value_len - 200;

 if ( (old_rt_field = OSLockBlock(char, value_block)) == NULL)
   {
     goto done;
   } 
 
 /* Allocate a buffer to hold the new data. */
 new_rt_field = malloc((WORD) newlen + sizeof(WORD));

 // Copy the new value to memory 
 memcpy(new_rt_field, old_rt_field, (WORD) newlen);

 OSUnlockBlock(value_block);

 if (err = NSFItemRealloc(item_block, &value_block, newlen))
   goto done;

 wsprintf(szBuff, "Reallocated to length 0x%08lx", newlen);
 
 new_block_ptr = OSLockBlock(char, value_block);
 if (new_block_ptr == NULL)
   {
     goto done;
   } 

 memcpy(new_block_ptr, new_rt_field, (WORD) newlen);
 
 OSUnlockBlock(value_block);
 NSFNoteUpdate(hNote, 0);
 
 free(new_rt_field);
 
```
**See Also :**
[NSFItemScan](/domino-c-api-docs/reference/Func/NSFItemScan)
[NSFItemInfo](/domino-c-api-docs/reference/Func/NSFItemInfo)
[NSFItemInfoNext](/domino-c-api-docs/reference/Func/NSFItemInfoNext)
[NSFItemQuery](/domino-c-api-docs/reference/Func/NSFItemQuery)
---
