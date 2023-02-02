##### Function : Text List Manipulation
##### ListGetSize - Returns the size of a text list.
---
##### #include <textlist.h>
WORD LNPUBLIC **ListGetSize(**

	void far *pList,
	BOOL  fPrefixDataType);
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
[ListAddEntry](D:/md_files/ListAddEntry.md)
[ListAddText](D:/md_files/ListAddText.md)
[ListAllocate](D:/md_files/ListAllocate.md)
[ListGetNumEntries](D:/md_files/ListGetNumEntries.md)
[ListGetText](D:/md_files/ListGetText.md)
[ListRemoveEntry](D:/md_files/ListRemoveEntry.md)
---
