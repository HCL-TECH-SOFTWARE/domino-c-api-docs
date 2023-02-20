##### Function : Database
##### NSFItemDefExtFree - Free the contents of the extended version of the Item Definition Table.

---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFItemDefExtFree(

	ITEM_DEFINITION_TABLE_EXT *ItemDeftable);
```
**Description :**

This function frees the contents of the extended version of the Item Definition 
Table contained in the ITEM_DEFINITION_TABLE_EXT structure and is used after 
the function NSFItemDefExtUnlock has been called. 

**Parameters :**
Input :
ItemDeftable  -  A pointer to the ITEM_DEFINITION_TABLE_EXT structure.  Call NSFDbItemDefTableExt to get a handle to this structure. 


Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[ITEM_DEFINITION_EXT](/reference/Data/ITEM_DEFINITION_EXT)
[ITEM_DEFINITION_TABLE_EXT](/reference/Data/ITEM_DEFINITION_TABLE_EXT)
[ITEM_DEFINITION_TABLE_LOCK](/reference/Data/ITEM_DEFINITION_TABLE_LOCK)
[NSFDbItemDefTableExt](/reference/Func/NSFDbItemDefTableExt)
[NSFItemDefExtEntries](/reference/Func/NSFItemDefExtEntries)
[NSFItemDefExtGetEntry](/reference/Func/NSFItemDefExtGetEntry)
[NSFItemDefExtLock](/reference/Func/NSFItemDefExtLock)
[NSFItemDefExtUnlock](/reference/Func/NSFItemDefExtUnlock)
---
