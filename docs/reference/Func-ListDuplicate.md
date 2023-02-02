##### Function : Text List Manipulation
##### ListDuplicate - Duplicate a text list.
---
##### #include <textlist.h>
STATUS LNPUBLIC **ListDuplicate(**

	LIST far *pInList,
	BOOL  fNoteItem,
	DHANDLE far *phOutList);
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
[ListAddText](D:/md_files/ListAddText.md)
[ListAllocate](D:/md_files/ListAllocate.md)
[ListGetNumEntries](D:/md_files/ListGetNumEntries.md)
[ListGetSize](D:/md_files/ListGetSize.md)
[ListRemoveAllEntries](D:/md_files/ListRemoveAllEntries.md)
[ListRemoveEntry](D:/md_files/ListRemoveEntry.md)
[ListAddEntry](D:/md_files/ListAddEntry.md)
---
