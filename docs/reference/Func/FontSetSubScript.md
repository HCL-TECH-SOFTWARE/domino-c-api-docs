##### Function : Font
##### FontSetSubScript - Turns on the SUBSCRIPT attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontSetSubScript(

	FONTID  fontid);
```
**Description :**

Implemented as a macro:

#define FontSetSubScript(fontid) ((DWORD)(fontid) | (ISSUB << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to set the SUBSCRIPT attribute.

Output :
(routine)  -  The specified FONTID with the SUBSCRIPT attribute turned on .



**See Also :**
[FontClearSubScript](/domino-c-api-docs/reference/Func/FontClearSubScript)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontIsSubScript](/domino-c-api-docs/reference/Func/FontIsSubScript)
---
