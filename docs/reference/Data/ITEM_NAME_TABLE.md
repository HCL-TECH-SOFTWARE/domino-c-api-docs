##### Data Type : Item (Field)
##### ITEM_NAME_TABLE - Header for list of item names.
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
   USHORT Length; /* total length of this buffer */
   USHORT Items; /* number of items in the table */
/* now comes an array of WORDS representing
   the lengths of the item names. */
/* now comes the item names as packed text */
} ITEM_NAME_TABLE;
```

**Description :**

<b>	</b>This is the header for lists of item names.<br>
<br>
This structure is followed by an array of WORD values containing the lengths, in bytes, of the item names;  there is one WORD for each item name in the table.  The array is followed, in turn, by the item names as packed data.


**See Also :**
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
[READ_MASK_xxx](/domino-c-api-docs/reference/Symb/READ_MASK_xxx)
---
