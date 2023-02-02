##### Data Type : Item (Field) Information
##### ITEM_DEFINITION_TABLE_LOCK - Database Item Definition Table (Extended) locked Information.
---
##### #include <nsfdb.h>
**Description :**
This structure is used with the ITEM_DEFINITION_TABLE_EXT and 
ITEM_DEFINITION_EXT structures that contain the Item Definition Table 
(Extended) information.  The information within this structure contains 
pointers to handles that are in the other structures, and some copies of other 
members.  The fields in this structure are:

Items       A copy of the number of items in the table
pItemDefArray      A pointer to ITEM_DEFINITION_EXT structures
ItemText       A pointer to packed text segments
NumSegments      A copy of the number of non-null segments of packed text.
ItemNameSegLengths[MAX_ITEMDEF_SEGMENTS] A copy of the length of each non-null 
text segment.
  
The user passes a pointer to this structure as input to the following NSF 
functions:
NSFItemDefExtLock, NSFItemDefExtUnlock, NSFItemDefExtEntries, 
NSFItemDefExtGetEntry

**See Also :**
[ITEM_DEFINITION_EXT](D:/md_files/ITEM_DEFINITION_EXT.md)
[ITEM_DEFINITION_TABLE_EXT](D:/md_files/ITEM_DEFINITION_TABLE_EXT.md)
[NSFDbItemDefTableExt](D:/md_files/NSFDbItemDefTableExt.md)
[NSFItemDefExtEntries](D:/md_files/NSFItemDefExtEntries.md)
[NSFItemDefExtFree](D:/md_files/NSFItemDefExtFree.md)
[NSFItemDefExtGetEntry](D:/md_files/NSFItemDefExtGetEntry.md)
[NSFItemDefExtLock](D:/md_files/NSFItemDefExtLock.md)
[NSFItemDefExtUnlock](D:/md_files/NSFItemDefExtUnlock.md)
---
