##### Function : Item (Field)
##### NSFItemQueryEx - Given BLOCKID of item, get all item and value info.
---
```
#include <nsfnote.h>
void LNPUBLIC NSFItemQueryEx(

	NOTEHANDLE  note_handle,
	BLOCKID  item_bid,
	char *item_name,
	WORD  return_buf_len,
	WORD *name_len_ptr,
	WORD *item_flags_ptr,
	WORD *value_datatype_ptr,
	BLOCKID *value_bid_ptr,
	DWORD *value_len_ptr,
	BYTE *retSeqByte,
	BYTE *retDupItemID);
```
**Description :**

This function takes a handle to an open note, the BLOCKID of any item in that 
note, and the length of the text buffer that is to receive the item name.  It 
returns all of the information that is typically required when appending an 
item using NSFItemAppendByBLOCKID: name, name length, flags, value data type, a 
BLOCKID associated with the value, and value length.  This function and 
NSFItemQuery are the only direct means of obtaining item flags.  The function 
NSFItemScan provides a callback routine which can also be used to obtain the 
contents of the item flags.

The BLOCKID values obtained using this function refer to memory within a note.  
This memory is managed by Domino and Notes, and should not be freed by the 
application.

**Parameters :**
Input :
note_handle  -  A handle to the open note you want to look in.

item_bid  -  The BLOCKID of a item in the note obtained from a call to  NSFItemInfo or NSFItemInfoNext.

return_buf_len  -  A Word containing the length of the text buffer.

Output :
item_name  -  Address of the text buffer in which the item name is returned.

name_len_ptr  -  Address of the WORD in which the actual length of item_name is returned.

item_flags_ptr  -  Address of the WORD in which the value of the item flags is returned.  

value_datatype_ptr  -  Address of the WORD in which the value data type is returned.

value_bid_ptr  -  Address of the BLOCKID in which the item value BLOCKID is returned.  Lock this BLOCKID by calling OSLockBlock. The resulting pointer always points to the datatype WORD, followed by the actual value. The data type word is always in Host format.  The value following the data type  word is in Domino Canonical format unless the data type is one of TYPE_TEXT,  TYPE_TEXT_LIST,   TYPE_USERID, TYPE_NUMBER, TYPE_NUMBER_RANGE,
TYPE_HIGHLIGHTS, TYPE_NOTEREF_LIST, TYPE_NOTELINK_LIST, TYPE_ERROR, or TYPE_UNAVAILABLE

value_len_ptr  -  Address of the DWORD in which the length of the item value is returned.  This length includes the Domino data type WORD that is prefixed to the actual data.

retSeqByte  -  Sequence byte.

retDupItemID  -  Duplicate item ID.


**Sample Usage :**
```
/* Find Item in Note1 and print the ITEM_FLAGS */

   if ( error_status = NSFItemInfo(note1_handle, TEXT_ITEM,
                           strlen(TEXT_ITEM), &item_bid,
                           NULL, NULL, NULL))
       goto Exit;

   NSFItemQueryEx(note1_handle, item_bid,
                item_name_buf, name_buf_len,
                &item_name_len, &item_flags, &value_type,
                &value_bid, &value_len
	        &retSeqByte, &retDupItemID);

   item_name_buf[item_name_len] = '\0';

   printf("Item %s has the following Item Flags set:\n",
          item_name_buf);

   if (item_flags & ITEM_SIGN)
       printf("\tITEM_SIGN\n");
   if (item_flags & ITEM_SEAL)
       printf("\tITEM_SEAL\n");
   if (item_flags & ITEM_SUMMARY)
       printf("\tITEM_SUMMARY\n");
   if (item_flags & ITEM_PROTECTED)
       printf("\tITEM_PROTECTED\n");
```
**See Also :**
[NSFItemAppendByBLOCKID](/reference/Func/NSFItemAppendByBLOCKID)
[NSFItemInfo](/reference/Func/NSFItemInfo)
[NSFItemInfoNext](/reference/Func/NSFItemInfoNext)
[NSFItemQuery](/reference/Func/NSFItemQuery)
[NSFItemScan](/reference/Func/NSFItemScan)
---
