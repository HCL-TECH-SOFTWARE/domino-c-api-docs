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
[ITEM_DEFINITION_EXT](/domino-c-api-docs/reference/Data/ITEM_DEFINITION_EXT)
[ITEM_DEFINITION_TABLE_EXT](/domino-c-api-docs/reference/Data/ITEM_DEFINITION_TABLE_EXT)
[ITEM_DEFINITION_TABLE_LOCK](/domino-c-api-docs/reference/Data/ITEM_DEFINITION_TABLE_LOCK)
[NSFDbItemDefTableExt](/domino-c-api-docs/reference/Func/NSFDbItemDefTableExt)
[NSFItemDefExtEntries](/domino-c-api-docs/reference/Func/NSFItemDefExtEntries)
[NSFItemDefExtGetEntry](/domino-c-api-docs/reference/Func/NSFItemDefExtGetEntry)
[NSFItemDefExtLock](/domino-c-api-docs/reference/Func/NSFItemDefExtLock)
[NSFItemDefExtUnlock](/domino-c-api-docs/reference/Func/NSFItemDefExtUnlock)
---
