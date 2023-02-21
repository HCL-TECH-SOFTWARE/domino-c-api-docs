##### Function : Font
##### FontIsEffect - Returns TRUE if the specified FONTID has the EFFECT attribute set, FALSE otherwise.
---
```
#include <fontid.h>
BOOL FontIsEffect(

	FONTID  fontid);
```
**Description :**

This routine tests if the EFFECT attribute is set in the specified FONTID.  
This attribute means that the text has a special effect style such as shadowed, 
embossed, or extruded text.

Implemented as a macro:

#define FontIsEffect(fontid) (((fontid) & ((DWORD) ISEFFECT << 
FONT_STYLE_SHIFT)) != 0)

**Parameters :**
Input :
fontid  -  The FONTID which is to be checked.

Output :
(routine)  -  TRUE if the EFFECT attribute is set, FALSE otherwise



**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontClearEffect](/domino-c-api-docs/reference/Func/FontClearEffect)
---
