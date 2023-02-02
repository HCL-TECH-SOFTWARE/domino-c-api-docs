##### Function : Database
##### NSFItemDefExtUnlock - Unlocks the contents of the extended version of the Item Definition Table.

---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFItemDefExtUnlock(**

	ITEM_DEFINITION_TABLE_EXT *ItemDefTable,
	ITEM_DEFINITION_TABLE_LOCK *ItemDefTableLock);
**Description :**
This function unlocks the contents of the ITEM_DEFINITION_TABLE_EXT structure, 
and is used with the following NSF functions: NSFItemDefExtEntries, 
NSFItemExtGetEntry, NSFItemDefExtLock, NSFItemDefExtFree.
**Parameters :**
Input :
ItemDefTable  -  A pointer to the ITEM_DEFINITION_TABLE_EXT structure.  Use NSFDbItemDefTableExt to receive a handle to this structure.



ItemDefTableLock  -  A pointer to an ITEM_DEFINITION_TABLE_LOCK structure.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Operation succeeded.



**See Also :**
[ITEM_DEFINITION_EXT](D:/md_files/ITEM_DEFINITION_EXT.md)
[ITEM_DEFINITION_TABLE_EXT](D:/md_files/ITEM_DEFINITION_TABLE_EXT.md)
[NSFDbItemDefTableExt](D:/md_files/NSFDbItemDefTableExt.md)
[NSFItemDefExtEntries](D:/md_files/NSFItemDefExtEntries.md)
[NSFItemDefExtFree](D:/md_files/NSFItemDefExtFree.md)
[NSFItemDefExtGetEntry](D:/md_files/NSFItemDefExtGetEntry.md)
[NSFItemDefExtLock](D:/md_files/NSFItemDefExtLock.md)
---
