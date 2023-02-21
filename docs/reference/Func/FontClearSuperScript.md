##### Function : Font
##### FontClearSuperScript - Turns off the SUPERSCRIPT attribute in the specified FONTID
---
```
#include <fontid.h>
FONTID FontClearSuperScript(

	FONTID  fontid);
```
**Description :**

Implemented as a macro:

#define FontClearSuperScript(fontid) ((DWORD)(fontid) & ~(ISSUPER << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to clear the SUPERSCRIPT attribute

Output :
(routine)  -  The specified FONTID with the SUPERSCRIPT attribute turned off



**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontIsSuperScript](/domino-c-api-docs/reference/Func/FontIsSuperScript)
[FontSetSuperScript](/domino-c-api-docs/reference/Func/FontSetSuperScript)
---
