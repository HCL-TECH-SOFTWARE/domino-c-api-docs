##### Data Type : Item (Field)
##### ITEM_VALUE_TABLE - Header for lists of data values
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
   USHORT Length; /* total length of this buffer */
   USHORT Items;  /* number of items in the table */
/* now comes an array of WORDS representing
   the lengths of the item values. */
/* now comes the item values as packed bytes */
} ITEM_VALUE_TABLE;
```

**Description :**

This is the header for lists of values with a variable number of entries having variable sizes.  The fields in the structure are:<br>
<br>
    Length - Total length of the block of memory.<br>
<br>
    Items - Number of items in the table.<br>
<br>
This structure is followed by an array of WORD values containing the lengths, in bytes, of the data items;  there is one WORD for each item in the table.  The data length table is followed, in turn, by a packed sequence of item values.  Each item value includes the item's datatype. The item's datatype is stored in the first USHORT of each item value.


**See Also :**
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
[READ_MASK_xxx](/domino-c-api-docs/reference/Symb/READ_MASK_xxx)
---
