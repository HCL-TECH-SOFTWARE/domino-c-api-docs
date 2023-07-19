##### Data Type : Item (Field) Information
##### ITEM_DEFINITION_TABLE_EXT - Database Item Definition Table (Extended)
---
```
#include <nsfdb.h>
```

**Definition :**

typedef struct {
   DWORD  Items;          /* number of items in the table */
   DWORD  ItemDefArray;   /* Memory handle of ITEM_DEFINITION_EXT
                             structures */
   DWORD  NumSegments;    /* Number of non-null segments in
                             ItemNameSegs */
   DHANDLE ItemNameSegs[MAX_ITEMDEF_SEGMENTS]; /* Segments of
                             packed text */
   DWORD  ItemNameSegLengths[MAX_ITEMDEF_SEGMENTS]; /* Length of
                             each non-null text segment */
} ITEM_DEFINITION_TABLE_EXT;

**Description :**

This table contains extended information for all the items defined in a database.   The fields in the structure are:
<ul><br>
<br>
Items							The number of items in the table<br>
ItemDefArray						Memory handle of ITEM_DEFINITION_EXT structures<br>
NumSegments						Number of non-null segments of packed text.<br>
ItemNameSegs[MAX_ITEMDEF_SEGMENTS]		An array of handles to non-null segments of packed text.<br>
ItemNameSegLengths[MAX_ITEMDEF_SEGMENTS]	Length of each non-null text segment.<br>
<br>
Use the following NSF functions to extract data from this structure:<br>
NSFItemDefExtEntries, NSFItemDefExtGetEntry.</ul>



**See Also :**
[ITEM_DEFINITION_EXT](/domino-c-api-docs/reference/Data/ITEM_DEFINITION_EXT)
[ITEM_DEFINITION_TABLE_LOCK](/domino-c-api-docs/reference/Data/ITEM_DEFINITION_TABLE_LOCK)
[NSFDbItemDefTableExt](/domino-c-api-docs/reference/Func/NSFDbItemDefTableExt)
[NSFItemDefExtEntries](/domino-c-api-docs/reference/Func/NSFItemDefExtEntries)
[NSFItemDefExtFree](/domino-c-api-docs/reference/Func/NSFItemDefExtFree)
[NSFItemDefExtGetEntry](/domino-c-api-docs/reference/Func/NSFItemDefExtGetEntry)
[NSFItemDefExtLock](/domino-c-api-docs/reference/Func/NSFItemDefExtLock)
[NSFItemDefExtUnlock](/domino-c-api-docs/reference/Func/NSFItemDefExtUnlock)
---
