##### Function : Dir
##### DirEntryItemDelete - Delete an item and all its values from an entry. 
---
```
#include <direntry.h>
STATUS LNPUBLIC DirEntryItemDelete(

	DIRENTRY  hEntry,
	const char *itemName);
```
**Description :**

Delete an item and all its values from an entry. No error is returned if the 
item does not exist. 
        Note that this routine only affects the in-memory hEntry object. The 
changes are written to the directory entry only after a subsequent 
DirEntryUpdate() operation on the hEntry.

**Parameters :**
Input :
hEntry  -  Handle to person entry whose item is to be deleted.

itemName  -  Name of the item to be deleted.

Output :
(routine)  -  NOERROR
ERR_DIR_NULL_ARGUMENT
If itemName is NULL. 
An ERR status on failure indicating the problem.



**See Also :**
[DirEntryItemAdd](/reference/Func/DirEntryItemAdd)
[DirEntryUpdate](/reference/Func/DirEntryUpdate)
---
