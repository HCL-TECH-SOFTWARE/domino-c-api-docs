##### Function : Database
##### NSFItemDefExtEntries - Get the number of items from the extended version of the database's Item Definition Table.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFItemDefExtEntries(

	ITEM_DEFINITION_TABLE_LOCK *ItemDefTableLock,
	DWORD *NumEntries);
```
**Description :**

This function gets the number of items from the extended version of the 
database's Item Definition Table.  This information is contained in the 
ITEM_DEFINITION_TABLE_EXT structure and  first use function 
NSFDbItemDefTableExt to get a handle to this structure.  Next lock this 
structure by calling function NSFItemDefExtLock before calling 
NSFItemDefExtEntries. 

**Parameters :**
Input :
ItemDefTableLock  -  A pointer to an ITEM_DEFINITION_TABLE_LOCK structure.


Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Operation succeeded.



NumEntries  -  A pointer to the number of items or entries in the ITEM_DEFINITION_TABLE_EXT structure.


**See Also :**
[ITEM_DEFINITION_EXT](/reference/Data/ITEM_DEFINITION_EXT)
[ITEM_DEFINITION_TABLE_EXT](/reference/Data/ITEM_DEFINITION_TABLE_EXT)
[ITEM_DEFINITION_TABLE_LOCK](/reference/Data/ITEM_DEFINITION_TABLE_LOCK)
[NSFDbItemDefTableExt](/reference/Func/NSFDbItemDefTableExt)
[NSFItemDefExtFree](/reference/Func/NSFItemDefExtFree)
[NSFItemDefExtGetEntry](/reference/Func/NSFItemDefExtGetEntry)
[NSFItemDefExtLock](/reference/Func/NSFItemDefExtLock)
[NSFItemDefExtUnlock](/reference/Func/NSFItemDefExtUnlock)
---
