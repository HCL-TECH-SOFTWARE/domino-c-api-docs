##### Function : Dir
##### DirEntryItemAdd - Overwrites the values of an entry item. 
---
```
#include <direntry.h>
STATUS LNPUBLIC DirEntryItemAdd(

	DIRENTRY  hEntry,
	const char *itemName,
	WORD  itemDataType,
	const void *itemVal,
	DWORD  itemValLen);
```
**Description :**

If the item does not exist then it is created. If it does already exist then 
its values are replaced. 
        Note that this routine only affects the in-memory hEntry object. The 
changes are written to the directory entry only after a subsequent 
DirEntryUpdate() operation on the hEntry.

**Parameters :**
Input :
hEntry  -  Handle to the entry whose item is to be modified.

itemName  -  Name of the item to be added.

itemDataType  -  The Notes data type of the new itemVal. See the section on Data Types for more information.

itemVal  -  Value to be added for itemName.

itemValLen  -  Size of itemVal in bytes.

Output :
(routine)  -  NOERROR
ERR_DIR_NULL_ARGUMENT
If hEntry, itemName, or itemVal are NULL. 
...
An ERR status on failure indicating the problem. 




**See Also :**
[DirEntryDelete](/reference/Func/DirEntryDelete)
[DirEntryFree](/reference/Func/DirEntryFree)
[DirEntryItemDelete](/reference/Func/DirEntryItemDelete)
[DirEntryUpdate](/reference/Func/DirEntryUpdate)
---
