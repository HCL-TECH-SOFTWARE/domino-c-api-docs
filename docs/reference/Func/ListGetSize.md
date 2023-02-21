##### Function : Text List Manipulation
##### ListGetSize - Returns the size of a text list.
---
```
#include <textlist.h>
WORD LNPUBLIC ListGetSize(

	void far *pList,
	BOOL  fPrefixDataType);
```
**Description :**

This function returns the size of the entire text list, including the Domino 
data type item prefix (if present) + the size of the LIST header + the size of 
the array containing offsets to the beginning of each entry, and the text of 
all entries.

**Parameters :**
Input :
pList  -  void far * containing the address of the LIST.

fPrefixDataType  -  BOOL indicating whether or not the text list is prefixed with a WORD containing the Domino data type.  TRUE if list was obtained from an existing note using NSFItemInfo and FALSE if the text list has just been created using ListAllocate.

Output :
(routine)  -  Return contains the size of the specified text list in BYTEs



**Sample Usage :**
```

   list_size = ListGetSize (list_ptr, prefix_flag);

```
**See Also :**
[ListAddEntry](/domino-c-api-docs/reference/Func/ListAddEntry)
[ListAddText](/domino-c-api-docs/reference/Func/ListAddText)
[ListAllocate](/domino-c-api-docs/reference/Func/ListAllocate)
[ListGetNumEntries](/domino-c-api-docs/reference/Func/ListGetNumEntries)
[ListGetText](/domino-c-api-docs/reference/Func/ListGetText)
[ListRemoveEntry](/domino-c-api-docs/reference/Func/ListRemoveEntry)
---
