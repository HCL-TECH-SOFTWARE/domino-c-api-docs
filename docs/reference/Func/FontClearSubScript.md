##### Function : Font
##### FontClearSubScript - Turns off the SUBSCRIPT attribute in the specified FONTID
---
```
#include <fontid.h>
FONTID FontClearSubScript(

	FONTID  fontid);
```
**Description :**

Implemented as a macro:

#define FontClearSubScript(fontid) ((DWORD)(fontid) & ~(ISSUB << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to clear the SUBSCRIPT attribute

Output :
(routine)  -  The specified FONTID with the SUBSCRIPT attribute turned off.



**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontIsSubScript](/domino-c-api-docs/reference/Func/FontIsSubScript)
[FontSetSubScript](/domino-c-api-docs/reference/Func/FontSetSubScript)
---
