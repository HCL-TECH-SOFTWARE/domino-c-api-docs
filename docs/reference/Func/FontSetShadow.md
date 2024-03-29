##### Function : Font
##### FontSetShadow - Turns on the SHADOW attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontSetShadow(

	FONTID  fontid);
```
**Description :**

This routine sets the SHADOW attribute in the specified FONTID.

Implemented as a macro:

#define FontSetShadow(fontid) ((DWORD)(fontid) | (ISSHADOW << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to set the SHADOW attribute.

Output :
(routine)  -  The specified FONTID with the SHADOW attribute turned on.



**See Also :**
[FontClearShadow](/domino-c-api-docs/reference/Func/FontClearShadow)
[FontGetShadowOffset](/domino-c-api-docs/reference/Func/FontGetShadowOffset)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
---
