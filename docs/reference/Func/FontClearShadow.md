##### Function : Font
##### FontClearShadow - Turns off the SHADOW attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontClearShadow(

	FONTID  fontid);
```
**Description :**

This routine turns off the SHADOW attribute in the specified FONTID.

Implemented as a macro:

#define FontClearShadow(fontid) ((DWORD)(fontid) & ~(ISSHADOW << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to clear the SHADOW attribute.

Output :
(routine)  -  The specified FONTID with the SHADOW attribute turned off.



**See Also :**
[FontSetShadow](/domino-c-api-docs/reference/Func/FontSetShadow)
[FontGetShadowOffset](/domino-c-api-docs/reference/Func/FontGetShadowOffset)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
---
