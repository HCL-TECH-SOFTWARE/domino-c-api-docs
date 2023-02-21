##### Function : Font
##### FontIsSubScript - Returns TRUE if the specified FONTID has the SUBSCRIPT attribute set, FALSE otherwise.
---
```
#include <fontid.h>
BOOL FontIsSubScript(

	FONTID  fontid);
```
**Description :**

Tests to see if the SUBSCRIPT attribute is set in the specified FONTID.  
Implemented as a macro:

#define FontIsSubScript(fontid) (((fontid) & ((DWORD)(ISEFFECT|ISSUB) << 
FONT_STYLE_SHIFT)) == (DWORD)(ISSUB << FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID which is to be checked.

Output :
(routine)  -  TRUE if the SUBSCRIPT attribute is set, FALSE otherwise.



**See Also :**
[FontClearSubScript](/domino-c-api-docs/reference/Func/FontClearSubScript)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontSetSubScript](/domino-c-api-docs/reference/Func/FontSetSubScript)
---
