##### Data Type : Item (Field) Information
##### ITEM_DEFINITION_EXT - Database Item Definition Table (Extended) Information
---
```
#include <nsfdb.h>
```

**Definition :**

typedef struct {
   DWORD ItemOffset;     /* offset into ItemNameSegs to item name */
   WORD  ItemType;       /* default data type of the item */
   WORD  ItemNameLength; /* length of the item's name */
} ITEM_DEFINITION_EXT;

**Description :**

This structure contains item information that is in the Item Definition Table (Extended) (see structure ITEM_DEFINITION_TABLE_EXT).  The fields in the structure are:
<ul><br>
<br>
ItemOffset							Offset into ItemNameSegs for item name<br>
ItemType 							Default data type of the item<br>
ItemNameLength						Length of the item's name</ul>



**See Also :**
[ITEM_DEFINITION_TABLE_EXT](/domino-c-api-docs/reference/Data/ITEM_DEFINITION_TABLE_EXT)
[ITEM_DEFINITION_TABLE_LOCK](/domino-c-api-docs/reference/Data/ITEM_DEFINITION_TABLE_LOCK)
[NSFItemDefExtEntries](/domino-c-api-docs/reference/Func/NSFItemDefExtEntries)
[NSFItemDefExtFree](/domino-c-api-docs/reference/Func/NSFItemDefExtFree)
[NSFItemDefExtGetEntry](/domino-c-api-docs/reference/Func/NSFItemDefExtGetEntry)
[NSFItemDefExtLock](/domino-c-api-docs/reference/Func/NSFItemDefExtLock)
[NSFItemDefExtUnlock](/domino-c-api-docs/reference/Func/NSFItemDefExtUnlock)
---
