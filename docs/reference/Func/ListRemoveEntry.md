##### Function : Text List Manipulation
##### ListRemoveEntry - Remove an entry from a text list.
---
```
#include <textlist.h>
STATUS LNPUBLIC ListRemoveEntry(

	DHANDLE  hList,
	BOOL  fPrefixDataType,
	WORD far *pListSize,
	WORD  EntryNumber);
```
**Description :**

This function removes the requested entry from a text list created by 
ListAllocate.  During the removal process, the Domino memory object containing 
the list is re-allocated and reduced in size by an amount corresponding the 
length of the text entry and its related header overhead.  If you had 
previously locked the list handle to obtain a pointer to the text list, be 
aware that this pointer may no longer valid after calling ListRemoveEntry().   
You must unlock the list handle and then re-lock the list handle after the call 
to ListRemoveEntry(), if you need to reference the pointer to the text list.

This function can not be used to decrease the size of a text list item that is 
already part of a note, as the value_blockid.pool member is not the equivalent 
of an hList.

**Parameters :**
Input :
hList  -  HANDLE to memory object containing text list.  This handle must have been returned by ListAllocate.

fPrefixDataType  -  BOOL indicating whether or not the list is prefixed with a WORD containing the Domino data type.  Should be FALSE when using a HANDLE to a newly created list that will later be added to a note using NSFItemAppend.

pListSize  -  Address of the WORD variable containing the current size of the text list.

EntryNumber  -  WORD containing index (0-based) of entry to be removed.  Should be in the range of 0 through (ListGetNumEntries - 1).

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include:

NOERROR - list entry was successfully removed.
ERR_ODS_NO_SUCH_ENTRY -  no such entry in the text list.


pListSize  -  Address of the WORD in which the new size of the text list, including  related overhead is returned


**Sample Usage :**
```

   if (error_status = ListRemoveEntry (list_handle, prefix_flag,
                                    &list_size, SECOND_ENTRY))
       goto Exit;

```
**See Also :**
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[ListAddEntry](/domino-c-api-docs/reference/Func/ListAddEntry)
[ListAddText](/domino-c-api-docs/reference/Func/ListAddText)
[ListGetSize](/domino-c-api-docs/reference/Func/ListGetSize)
[ListGetNumEntries](/domino-c-api-docs/reference/Func/ListGetNumEntries)
---
