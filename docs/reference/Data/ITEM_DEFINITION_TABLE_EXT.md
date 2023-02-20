##### Data Type : Item (Field) Information
##### ITEM_DEFINITION_TABLE_EXT - Database Item Definition Table (Extended)
---
```
#include <nsfdb.h>
```
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
[ITEM_DEFINITION_EXT](/reference/Data/ITEM_DEFINITION_EXT)
[ITEM_DEFINITION_TABLE_LOCK](/reference/Data/ITEM_DEFINITION_TABLE_LOCK)
[NSFDbItemDefTableExt](/reference/Func/NSFDbItemDefTableExt)
[NSFItemDefExtEntries](/reference/Func/NSFItemDefExtEntries)
[NSFItemDefExtFree](/reference/Func/NSFItemDefExtFree)
[NSFItemDefExtGetEntry](/reference/Func/NSFItemDefExtGetEntry)
[NSFItemDefExtLock](/reference/Func/NSFItemDefExtLock)
[NSFItemDefExtUnlock](/reference/Func/NSFItemDefExtUnlock)
---
