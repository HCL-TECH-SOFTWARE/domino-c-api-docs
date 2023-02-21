##### Function : Text List Manipulation
##### ListRemoveAllEntries - Remove all entries from a text list.
---
```
#include <textlist.h>
STATUS LNPUBLIC ListRemoveAllEntries(

	DHANDLE  hList,
	BOOL  fPrefixDataType,
	WORD far *pListSize);
```
**Description :**

Remove all the entries from the text list.  During the removal process, the 
Domino memory object containing the list is re-allocated and the size will be 
reduced to the minimum size for a text list.  If you had previously locked the 
list handle to obtain a pointer to the text list, be aware that this pointer 
may no longer valid after calling ListRemoveAllEntries().   You must unlock the 
list handle and then re-lock the list handle after the call to 
ListRemoveAllEntries(), if you need to reference the pointer to the text list.

**Parameters :**
Input :
hList  -  HANDLE to a Domino memory object containing text list.  This handle must have been created with ListAllocate.  ListAddEntry does not require that the list be unlocked at the time of the call.

fPrefixDataType  -  BOOL indicating whether or not the list is prefixed with a WORD containing the Domino data type.

pListSize  -  Address of the WORD variable containing the current list size.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


pListSize  -  Address of the WORD variable containing the new list size.


**See Also :**
[ListAddEntry](/domino-c-api-docs/reference/Func/ListAddEntry)
[ListAddText](/domino-c-api-docs/reference/Func/ListAddText)
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[ListGetNumEntries](/domino-c-api-docs/reference/Func/ListGetNumEntries)
[ListGetSize](/domino-c-api-docs/reference/Func/ListGetSize)
[ListRemoveEntry](/domino-c-api-docs/reference/Func/ListRemoveEntry)
---
