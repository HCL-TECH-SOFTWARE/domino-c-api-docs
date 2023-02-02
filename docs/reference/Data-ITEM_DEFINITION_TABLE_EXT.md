##### Data Type : Item (Field) Information
##### ITEM_DEFINITION_TABLE_EXT - Database Item Definition Table (Extended)
---
##### #include <nsfdb.h>
**Description :**
This table contains extended information for all the items defined in a 
database.   The fields in the structure are:

Items       The number of items in the table
ItemDefArray      Memory handle of ITEM_DEFINITION_EXT structures
NumSegments      Number of non-null segments of packed text.
ItemNameSegs[MAX_ITEMDEF_SEGMENTS]  An array of handles to non-null segments of 
packed text.
ItemNameSegLengths[MAX_ITEMDEF_SEGMENTS] Length of each non-null text segment.

Use the following NSF functions to extract data from this structure:
NSFItemDefExtEntries, NSFItemDefExtGetEntry.

**See Also :**
[ITEM_DEFINITION_EXT](D:/md_files/ITEM_DEFINITION_EXT.md)
[ITEM_DEFINITION_TABLE_LOCK](D:/md_files/ITEM_DEFINITION_TABLE_LOCK.md)
[NSFDbItemDefTableExt](D:/md_files/NSFDbItemDefTableExt.md)
[NSFItemDefExtEntries](D:/md_files/NSFItemDefExtEntries.md)
[NSFItemDefExtFree](D:/md_files/NSFItemDefExtFree.md)
[NSFItemDefExtGetEntry](D:/md_files/NSFItemDefExtGetEntry.md)
[NSFItemDefExtLock](D:/md_files/NSFItemDefExtLock.md)
[NSFItemDefExtUnlock](D:/md_files/NSFItemDefExtUnlock.md)
---
