##### Function : Item (Field)
##### NSFItemInfo - Get information about an item (field) in a note.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFItemInfo(**

	NOTEHANDLE  note_handle,
	const char far *item_name,
	WORD  name_len,
	BLOCKID far *item_blockid,
	WORD far *value_datatype,
	BLOCKID far *value_blockid,
	DWORD far *value_len);
**Description :**
This function gets information about a particular item (field) in a note. The 
function's inputs are a handle to an open note and the name of the field you 
are looking for. It yields the item header, the data type, the item's value, 
and the length of the item's value.

Items in a note are ordered. You can get information about the first item in 
the note, regardless of its name, by specifying NULL for the field name.

The BLOCKID values obtained using this function refer to memory within a note.  
This memory is managed by Domino and Notes, and should not be freed by the 
application.
**Parameters :**
Input :
note_handle  -  A handle to the open note you want to look in.

item_name  -  The name of the item (field) you want information about. To get information about the first field in the note, regardless of its name, set this argument to NULL.

name_len  -  The length of item_name. If the item_name is NULL, set this argument to zero.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_ITEM_NOT_FOUND


item_blockid  -  The address of a BLOCKID in which the pool and block of an item's header is returned. Set this argument to NULL if you don't want this information. You need the BLOCKID of the item's header to pass as input arguments to API functions such as NSFItemInfoNext, NSFItemQuery, NSFItemCopy, and NSFItemDeleteByBLOCKID.

value_datatype  -  The address of a WORD in which the data type of the item's value is returned. The data types are defined in TYPE_xxx.  In the case where ERR_ITEM_NOT_FOUND is returned by NSFItemInfo(), this argument is always set to TYPE_INVALID_OR_UNKNOWN.  

value_blockid  -  The address of a BLOCKID in which the pool and block of the item's value (the actual contents of the field) is returned. You must call OSLockBlock to translate the BLOCKID into an actual address.  The first 2 bytes pointed to are the item's datatype WORD, followed by the item's actual value. The data type word is always in host (machine-specific) format.  The remainder of the data is also in host format, unless the data type is one of:  TYPE_COMPOSITE, TYPE_COLLATION, TYPE_OBJECT, TYPE_VIEW_FORMAT, TYPE_ICON, TYPE_SIGNATURE, TYPE_SEAL, TYPE_SEALDATA, TYPE_SEAL_LIST, TYPE_WORKSHEET_DATA, or TYPE_USERDATA. If the item is one of these data types, you must convert the data structures in the item's value from Domino canonical format to host format before accessing the members of those structures.

value_len  -  The address of a DWORD in which the length of the item's value is returned.  The length of the datatype WORD that precedes the value is always included in the length that is returned.

**Sample Usage :**
```
   /* Obtain the old list */

   if (error_status = NSFItemInfo(note_handle, ITEM_NAME,
                                  strlen(ITEM_NAME), &item_bid,
                                  &value_datatype, &value_bid,
                                  &value_size))
       goto Exit;

   old_list_ptr = OSLockBlock(char, value_bid);

   if (old_list_ptr != NULL)
       cleanup_state += UNLOCK_VALUEBID;

  /* Step over the data type word to point to the actual data */
   old_list_ptr += sizeof(WORD);

```
**See Also :**
[NSFItemInfoNext](D:/md_files/NSFItemInfoNext.md)
[NSFItemScan](D:/md_files/NSFItemScan.md)
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
[ODSReadMemory](D:/md_files/ODSReadMemory.md)
[ODSWriteMemory](D:/md_files/ODSWriteMemory.md)
[OSLockBlock](D:/md_files/OSLockBlock.md)
[TYPE_xxx](D:/md_files/TYPE_xxx.md)
---
