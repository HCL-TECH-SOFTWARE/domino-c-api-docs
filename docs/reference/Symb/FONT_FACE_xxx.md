##### Symbolic Value : Miscellaneous
##### FONT_FACE_xxx - BYTE values for Face member of FONTIDFIELDS.
---
```
#include <fontid.h>
```
**Description :**

These symbols define the standard type faces identified in the Face member of a 
FONTIDFIELDS structure.

The Face member of the FONTIDFIELDS structure may be either one of these 
standard font faces, or a font ID resolved by a font table.  A Face member 
value greater than or equal to STATIC_FONT_FACES (5) refers to an entry in a 
font table. See Data Type CDFONTTABLE.

**See Also :**
[CDFONTTABLE](/domino-c-api-docs/reference/Data/CDFONTTABLE)
[CDTEXT](/domino-c-api-docs/reference/Data/CDTEXT)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[ISxxx](/domino-c-api-docs/reference/Symb/ISxxx)
[NOTES_COLOR_xxx](/domino-c-api-docs/reference/Symb/NOTES_COLOR_xxx)
[STATIC_FONT_FACES](/domino-c-api-docs/reference/Symb/STATIC_FONT_FACES)
---
