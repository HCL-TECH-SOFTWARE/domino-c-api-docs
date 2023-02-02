##### Function : Item (Field)
##### NSFItemAppend - Adds an item (field) to an open note using the item name.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFItemAppend(**

	NOTEHANDLE  note_handle,
	WORD  item_flags,
	const char far *item_name,
	WORD  name_len,
	WORD  item_type,
	const void far *item_value,
	DWORD  value_len);
**Description :**
This function adds an item (field) to an open note. It does not update the 
Domino database file on disk. To write the modified note to the database file 
on disk, you must call NSFNoteUpdate after appending all items to the note.

NSFItemAppend is a flexible, low-level way to add an item to a note. You must 
specify, as input, the item name, the data, the data type, and the data 
length.  The API also provides less flexible, higher-level functions such as 
NSFItemSetText for appending items of specific data types.

NSFItemAppend creates an item header and adds this item header to a queue 
associated with the open note. You may append any number of items to a note 
through repeated calls to NSFItemAppend. NSFItemAppend also allocates a block 
of memory to store the item value. It copies the number of bytes specified by 
value_len from the buffer specified by item_value into this memory block. This 
means that after NSFItemAppend has returned, your program may free the memory 
specified by item_value.

The data pointed to by item_value does not begin with the data type word.  The 
format of the data pointed to by item_value depends on the data type. The 
reference manual entry for each data type specifies the format of the item 
value.

For each of the following data types, the data pointed to by item_value must be 
in Domino canonical format.  Your program must convert the item value to Domino 
canonical Format before calling NSFItemAppend if (1) your program runs on a 
non-Intel architecture machine, and (2) item_type is one of the following data 
types: 

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

Use ODSWriteMemory() to convert item data from machine-specific (host) format 
to Domino canonical format before calling NSFItemAppend.
**Parameters :**
Input :
note_handle  -  The handle to the note that will receive this item.

item_flags  -  The flags that define the characteristics of this item. These flags are defined in ITEM_xxx and may be bitwise or'ed together for combined functionality.

item_name  -  The name of the item in the note. This name is equivalent to the field name when you design a form using the screen interface. 

name_len  -  The length of item_name.

item_type  -  The type of data in this item. Item types are defined in TYPE_xxx.

item_value  -  A pointer to the value (excluding the data type word).  If the API program is running on a non-Intel architecture system and item_type is one of the data types listed above, then the data pointed to by item_value must be in Domino canonical format.

value_len  -  The length of the item's value (excluding the data type word). The length must not exceed 64K bytes. If the ITEM_SUMMARY flag is set in item_flags, then value_len must not exceed 32K.

Output :
(routine)  -  cReturn status from this call: 

NOERROR - Successfully appended Item to the note.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


**Sample Usage :**
```


   /* Prepare to and then append the text list */

   list_size    = ListGetSize (list_ptr, prefix_flag);
   if (error_status = NSFItemAppend(note_handle,0,
                               "Form", strlen("Form"),
                               TYPE_TEXT, argv[2],
                               (DWORD) strlen(argv[2])))
       goto Exit;
   if (error_status = NSFItemAppend(note_handle,ITEM_SUMMARY,
                               ITEM_NAME, strlen(ITEM_NAME),
                               TYPE_TEXT_LIST, list_ptr,
                               (DWORD) list_size))
       goto Exit;

```
**See Also :**
[ITEM_xxx](D:/md_files/ITEM_xxx.md)
[NSFItemAppendByBLOCKID](D:/md_files/NSFItemAppendByBLOCKID.md)
[NSFItemDelete](D:/md_files/NSFItemDelete.md)
[NSFItemDeleteByBLOCKID](D:/md_files/NSFItemDeleteByBLOCKID.md)
[NSFItemSetNumber](D:/md_files/NSFItemSetNumber.md)
[NSFItemSetText](D:/md_files/NSFItemSetText.md)
[NSFItemSetTime](D:/md_files/NSFItemSetTime.md)
[ODSLength](D:/md_files/ODSLength.md)
[ODSWriteMemory](D:/md_files/ODSWriteMemory.md)
[TYPE_xxx](D:/md_files/TYPE_xxx.md)
---
