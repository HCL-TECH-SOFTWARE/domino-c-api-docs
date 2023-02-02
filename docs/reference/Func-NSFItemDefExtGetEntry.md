##### Function : Database
##### NSFItemDefExtGetEntry - Get an item entry from the extended version of the database's Item Definition Table.

---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFItemDefExtGetEntry(**

	ITEM_DEFINITION_TABLE_LOCK *ItemDefTableLock,
	DWORD  ItemNum,
	WORD *ItemType,
	WORD *ItemLength,
	char **ItemName);
**Description :**
This function gets an item entry from the extended version of the database's 
Item Definition Table.  After first getting the handle to the 
ITEM_DEFINITION_TABLE_EXT structure with function NSFDbItemDefTableExt, locking 
the structure with NSFItemDefExtLock, and getting the number of items in the 
table with NSFItemDefExtEntries, use this function to get the Item Type, Item 
Length, and Item Name of the specifed item number that was passed in.
**Parameters :**
Input :
ItemDefTableLock  -  A pointer to an ITEM_DEFINITION_TABLE_LOCK structure.


ItemNum  -  The item number of the item entry.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Operation succeeded.



ItemType  -  A pointer to the Item Type.

ItemLength  -  A pointer to the Item Length.  Use this length when accessing the Item Name which is not null terminated.

ItemName  -  The address of a pointer to the Item Name.  This parameter is not null terminated.  Use the Item Length and null terminate the character stream.

**See Also :**
[ITEM_DEFINITION_EXT](D:/md_files/ITEM_DEFINITION_EXT.md)
[ITEM_DEFINITION_TABLE_EXT](D:/md_files/ITEM_DEFINITION_TABLE_EXT.md)
[ITEM_DEFINITION_TABLE_LOCK](D:/md_files/ITEM_DEFINITION_TABLE_LOCK.md)
[NSFDbItemDefTableExt](D:/md_files/NSFDbItemDefTableExt.md)
[NSFItemDefExtEntries](D:/md_files/NSFItemDefExtEntries.md)
[NSFItemDefExtFree](D:/md_files/NSFItemDefExtFree.md)
[NSFItemDefExtLock](D:/md_files/NSFItemDefExtLock.md)
[NSFItemDefExtUnlock](D:/md_files/NSFItemDefExtUnlock.md)
---
