##### Function : Database
##### NSFItemDefExtEntries - Get the number of items from the extended version of the database's Item Definition Table.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFItemDefExtEntries(**

	ITEM_DEFINITION_TABLE_LOCK *ItemDefTableLock,
	DWORD *NumEntries);
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
[ITEM_DEFINITION_EXT](D:/md_files/ITEM_DEFINITION_EXT.md)
[ITEM_DEFINITION_TABLE_EXT](D:/md_files/ITEM_DEFINITION_TABLE_EXT.md)
[ITEM_DEFINITION_TABLE_LOCK](D:/md_files/ITEM_DEFINITION_TABLE_LOCK.md)
[NSFDbItemDefTableExt](D:/md_files/NSFDbItemDefTableExt.md)
[NSFItemDefExtFree](D:/md_files/NSFItemDefExtFree.md)
[NSFItemDefExtGetEntry](D:/md_files/NSFItemDefExtGetEntry.md)
[NSFItemDefExtLock](D:/md_files/NSFItemDefExtLock.md)
[NSFItemDefExtUnlock](D:/md_files/NSFItemDefExtUnlock.md)
---
