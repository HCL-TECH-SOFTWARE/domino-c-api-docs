##### Function : Database
##### NSFItemDefExtFree - Free the contents of the extended version of the Item Definition Table.

---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFItemDefExtFree(**

	ITEM_DEFINITION_TABLE_EXT *ItemDeftable);
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
[ITEM_DEFINITION_EXT](D:/md_files/ITEM_DEFINITION_EXT.md)
[ITEM_DEFINITION_TABLE_EXT](D:/md_files/ITEM_DEFINITION_TABLE_EXT.md)
[ITEM_DEFINITION_TABLE_LOCK](D:/md_files/ITEM_DEFINITION_TABLE_LOCK.md)
[NSFDbItemDefTableExt](D:/md_files/NSFDbItemDefTableExt.md)
[NSFItemDefExtEntries](D:/md_files/NSFItemDefExtEntries.md)
[NSFItemDefExtGetEntry](D:/md_files/NSFItemDefExtGetEntry.md)
[NSFItemDefExtLock](D:/md_files/NSFItemDefExtLock.md)
[NSFItemDefExtUnlock](D:/md_files/NSFItemDefExtUnlock.md)
---
