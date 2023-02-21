##### Function : Text List Manipulation
##### ListDuplicate - Duplicate a text list.
---
```
#include <textlist.h>
STATUS LNPUBLIC ListDuplicate(

	LIST far *pInList,
	BOOL  fNoteItem,
	DHANDLE far *phOutList);
```
**Description :**

This function creates a duplicate copy of a text list.

**Parameters :**
Input :
pInList  -  Pointer to the source text list that is to be duplicated.

fNoteItem  -  Indicates whether or not the text list is prefixed with a WORD containing the Domino data type.  TRUE if the list contains this prefix.  A list obtained from NSFItemInfo() contains this prefix.  A list created with ListAllocate does not contain this prefix.

Output :
(routine)  -  Return status from this call - indicates either success (NOERROR), or one of the following:

ERR_MEMORY - Not enough global memory available for allocation.
ERR_SEGMENT_TOO_BIG - Requested size is greater than the maximum supported.


phOutList  -  Handle to the duplicate copy of the source text list.


**See Also :**
[ListAddText](/domino-c-api-docs/reference/Func/ListAddText)
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[ListGetNumEntries](/domino-c-api-docs/reference/Func/ListGetNumEntries)
[ListGetSize](/domino-c-api-docs/reference/Func/ListGetSize)
[ListRemoveAllEntries](/domino-c-api-docs/reference/Func/ListRemoveAllEntries)
[ListRemoveEntry](/domino-c-api-docs/reference/Func/ListRemoveEntry)
[ListAddEntry](/domino-c-api-docs/reference/Func/ListAddEntry)
---
