##### Symbolic Value : Miscellaneous
##### STATIC_FONT_FACES - Used to determine whether a font table entry for a specified font must be generated.
---
```
#include <fontid.h>
```

**Symbolic Values :**



**Description :**

The symbols FONT_FACE_xxx define the standard type faces identified in the Face member of a FONTIDFIELDS structure.  The Face member of the FONTIDFIELDS structure may be any one of these standard font faces, or a font ID resolved by a font table.  A Face member value greater than or equal to STATIC_FONT_FACES (5) refers to an entry in a font table.  See Data Type CDFONTTABLE.


**See Also :**
[CDFONTTABLE](/domino-c-api-docs/reference/Data/CDFONTTABLE)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FONT_FACE_xxx](/domino-c-api-docs/reference/Symb/FONT_FACE_xxx)
---
