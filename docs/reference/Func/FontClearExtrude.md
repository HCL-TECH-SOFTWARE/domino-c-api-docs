##### Function : Font
##### FontClearExtrude - Turns off the EXTRUDE attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontClearExtrude(

	FONTID  fontid);
```
**Description :**

This function turns off the EXTRUDE attribute in the specified FONTID.  Text 
that has the EXTRUDE attribute appears to be pushed into the page.

Implemented as a macro:

#define FontClearExtrude(fontid) ((DWORD)(fontid) & ~(ISEXTRUDE << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to clear the EXTRUDE attribute.

Output :
(routine)  -  The specified FONTID with the EXTRUDE attribute turned off.



**See Also :**
[FontSetExtrude](/domino-c-api-docs/reference/Func/FontSetExtrude)
[FontIsExtrude](/domino-c-api-docs/reference/Func/FontIsExtrude)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
---
