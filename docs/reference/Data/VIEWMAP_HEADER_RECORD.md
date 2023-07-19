##### Data Type : Navigators
##### VIEWMAP_HEADER_RECORD - Header CD record for Navigator layout.
---
```
#include <vmods.h>
```

**Definition :**

typedef struct {
   BSIG Header;
   WORD Version; /* (see VIEWMAP_VERSION) */
   WORD NameLen;
} VIEWMAP_HEADER_RECORD;

**Description :**

The VIEWMAP_HEADER_RECORD is the first record in an item of type TYPE_VIEWMAP_LAYOUT, the graphical layout of a Navigator.  The fields in this structure are:
<ul><br>

<ul>Header		Identfies this record as a VIEWMAP_HEADER_RECORD.<br>
Version		Version number of Navigator record formats.  Use VIEWMAP_VERSION value.<br>
NameLen	Reserved for future use.   Set to 0. </ul>
</ul>



**See Also :**
[VIEWMAP_VERSION](/domino-c-api-docs/reference/Symb/VIEWMAP_VERSION)
---
