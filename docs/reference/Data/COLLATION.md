##### Data Type : Views
##### COLLATION - Defines sorting information for the columns in a view note.
---
```
#include <nifcoll.h>
```

**Definition :**
```
typedef struct {
   USHORT BufferSize;  /* Size of entire buffer in bytes */
   USHORT Items;       /* Number of items following */
   BYTE   Flags;       /* See COLLATION_FLAG_xxx */
   BYTE   signature;   /* Must be COLLATION_SIGNATURE */
/* COLLATE_DESCRIPTOR desc[];  ** COLLATE_DESCRIPTORs follow */
/* char text_area[];   ** followed by variable length text */
} COLLATION;
```

**Description :**

This structure is used to specify the manner in which data in a view is sorted.  The COLLATION structure, along with its associated COLLATE_DESCRIPTOR structures and character strings, comprise the $Collation item in a view note.<br>
<br>
BufferSize = total size in bytes of the $Collation item.<br>
Items          = number of columns in the view that are sorted or categorized.<br>
Flags         =  Optional.  May be set to a COLLATION_FLAG_xxx value.  Otherwise, set to 0.<br>
Signature = COLLATION_SIGNATURE.<br>
<br>
These values are immediately followed by an array of COLLATE_DESCRIPTOR structures, one for each sorted column.  The collation descriptor array is followed by a sequence of packed character strings relevant to those descriptors.  See the definition of COLLATE_DESCRIPTOR for more details.<br>



**See Also :**
[COLLATE_DESCRIPTOR](/domino-c-api-docs/reference/Data/COLLATE_DESCRIPTOR)
[COLLATION_FLAG_xxx](/domino-c-api-docs/reference/Symb/COLLATION_FLAG_xxx)
---
