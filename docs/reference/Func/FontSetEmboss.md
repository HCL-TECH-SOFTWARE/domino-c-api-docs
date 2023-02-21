##### Function : Font
##### FontSetEmboss - Turns on the EMBOSS attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontSetEmboss(

	FONTID  fontid);
```
**Description :**

This routine sets the EMBOSS attribute in the specified FONTID.  Text that has 
the EMBOSS attribute appears to be sticking out of the page.

Implemented as a macro:

#define FontSetEmboss(fontid) ((DWORD)(fontid) | (ISEMBOSS << FONT_STYLE_SHIFT))

The EMBOSS attribute and the EXTRUDE attribute are mutually exclusive.  When 
setting the EMBOSS attribute, make sure the EXTRUDE attribute is cleared.

**Parameters :**
Input :
fontid  -  The FONTID in which to set the EMBOSS attribute.

Output :
(routine)  -  The specified FONTID with the EMBOSS attribute turned on.



**See Also :**
[FontClearEmboss](/domino-c-api-docs/reference/Func/FontClearEmboss)
[FontIsEmboss](/domino-c-api-docs/reference/Func/FontIsEmboss)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
---
