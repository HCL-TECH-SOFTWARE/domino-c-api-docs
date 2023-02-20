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
[CDFONTTABLE](/reference/Data/CDFONTTABLE)
[CDTEXT](/reference/Data/CDTEXT)
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
[ISxxx](/reference/Symb/ISxxx)
[NOTES_COLOR_xxx](/reference/Symb/NOTES_COLOR_xxx)
[STATIC_FONT_FACES](/reference/Symb/STATIC_FONT_FACES)
---
