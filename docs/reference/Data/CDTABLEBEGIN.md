##### Data Type : Composite Data
##### CDTABLEBEGIN - Specifies the beginning of a table.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   BSIG Header;
   WORD LeftMargin;            /* TWIPS */
   WORD HorizInterCellSpace;   /* TWIPS */
   WORD VertInterCellSpace;    /* TWIPS */
   WORD V4HorizInterCellSpace; /* TWIPS -- field was spare in V3 */
   WORD V4VertInterCellSpace;  /* TWIPS -- field was spare in V3 */
   WORD Flags;                 /* Flags (CDTABLE_xxx) */
} CDTABLEBEGIN;

**Description :**

This structure specifies the beginning of a table.  It contains information about the format and size of the table.    Use this structure when accessing a table in a rich text field.  As of R5, this structure is preceded by a CDPRETABLEBEGIN structure.  The CDPRETABLEBEGIN structure specifies additional table properties.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.


**See Also :**
[CDTABLEEND](/domino-c-api-docs/reference/Data/CDTABLEEND)
[CDTABLECELL](/domino-c-api-docs/reference/Data/CDTABLECELL)
[CDTABLE_xxx](/domino-c-api-docs/reference/Symb/CDTABLE_xxx)
[CDPRETABLEBEGIN](/domino-c-api-docs/reference/Data/CDPRETABLEBEGIN)
---
