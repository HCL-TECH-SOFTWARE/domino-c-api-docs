##### Function : Database
##### NSFItemDefExtLock - Locks the contents of the extended version of the Item Definition Table.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFItemDefExtLock(

	ITEM_DEFINITION_TABLE_EXT *ItemDefTable,
	ITEM_DEFINITION_TABLE_LOCK *ItemDefTableLock);
```
**Description :**

This function locks the contents of the ITEM_DEFINITION_TABLE_EXT structure, 
and is used with the following NSF functions: NSFItemDefExtEntries, 
NSFItemExtGetEntry, NSFItemDefExtUnlock, NSFItemDefExtFree.


**Parameters :**
Input :
ItemDefTable  -  A pointer to the ITEM_DEFINITION_TABLE_EXT structure.  Use NSFDbItemDefTableExt to receive a handle to this structure.

ItemDefTableLock  -  A pointer to an ITEM_DEFINITION_TABLE_LOCK structure.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Operation succeeded.




**See Also :**
[ITEM_DEFINITION_EXT](/domino-c-api-docs/reference/Data/ITEM_DEFINITION_EXT)
[ITEM_DEFINITION_TABLE_EXT](/domino-c-api-docs/reference/Data/ITEM_DEFINITION_TABLE_EXT)
[NSFDbItemDefTableExt](/domino-c-api-docs/reference/Func/NSFDbItemDefTableExt)
[NSFItemDefExtEntries](/domino-c-api-docs/reference/Func/NSFItemDefExtEntries)
[NSFItemDefExtFree](/domino-c-api-docs/reference/Func/NSFItemDefExtFree)
[NSFItemDefExtGetEntry](/domino-c-api-docs/reference/Func/NSFItemDefExtGetEntry)
[NSFItemDefExtUnlock](/domino-c-api-docs/reference/Func/NSFItemDefExtUnlock)
---
