##### Function : Text List Manipulation
##### ListGetText - Obtain a string from a text list.
---
```
#include <textlist.h>
STATUS LNPUBLIC ListGetText(

	void far *pList,
	BOOL  fPrefixDataType,
	WORD  EntryNumber,
	char far * far *retTextPointer,
	WORD far *retTextLength);
```
**Description :**

This function obtains a specific entry from an existing text list, then returns 
that text entry and its length.  If OSLockBlock is used with a value_blockid 
returned by NSFItemInfo, the pointer returned by OSLockBlock contains the 
address of the text list within the text list item of the existing note.  This 
function can then be used to obtain any string already in the text list item. 

**Parameters :**
Input :
pList  -  Pointer to memory containing the text list.

fPrefixDataType  -  BOOL indicating whether or not the list is prefixed with a WORD containing the Domino data type.  TRUE when using a pointer value derived from a BLOCKID obtained from NSFItemInfo or FALSE if using a pointer value to a newly created list, that will later be added to a note using NSFItemAppend.

EntryNumber  -  WORD containing the index (0-based) of the entry to retrieved.   The value should always be in a range between 0 and the value returned by (ListGetNumEntries - 1).

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include:

NOERROR - list entry was successfully located.
ERR_ODS_NO_SUCH_ENTRY -  no such entry in the text list.


retTextPointer  -  The address of a pointer in which a pointer to the requested text list entry is returned.  The text must then be copied/moved to pre-allocated storage.  The NULL terminator is not provided by the function.

retTextLength  -  The address of a WORD in which the size of the text list entry is returned.  This can be used to place a NULL terminator if you intend to create a null-terminated string using the text list entry.


**Sample Usage :**
```

   for (curr_entry_num = FIRST_ENTRY; curr_entry_num < last_entry_num;
        curr_entry_num++)
   {
       if (error_status = ListGetText(old_list_ptr, old_prefix_flag,
                                      curr_entry_num,
                                      &string_ptr, &string_length))
           break;
       if (error_status = ListAddEntry (list_handle, prefix_flag,
                                        &list_size, curr_entry_num,
                                        string_ptr, string_length))
           break;
   }

```
**See Also :**
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[ListAddEntry](/domino-c-api-docs/reference/Func/ListAddEntry)
[ListAddText](/domino-c-api-docs/reference/Func/ListAddText)
[ListRemoveEntry](/domino-c-api-docs/reference/Func/ListRemoveEntry)
[ListGetSize](/domino-c-api-docs/reference/Func/ListGetSize)
[ListGetNumEntries](/domino-c-api-docs/reference/Func/ListGetNumEntries)
---
