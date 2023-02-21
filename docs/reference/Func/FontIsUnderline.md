##### Function : Font
##### FontIsUnderline - Returns TRUE if the specified FONTID has the UNDERLINE attribute set, FALSE otherwise.
---
```
#include <fontid.h>
BOOL FontIsUnderline(

	FONTID  fontid);
```
**Description :**

Tests to see if the UNDERLINE attribute is set in the specified FONTID.  
Implemented as a macro:

#define FontIsUnderline(fontid) (((fontid) & ((DWORD) ISUNDERLINE << 
FONT_STYLE_SHIFT)) != 0)

**Parameters :**
Input :
fontid  -  The FONTID which is to be checked.

Output :
(routine)  -  TRUE if the UNDERLINE attribute is set, FALSE otherwise.



**See Also :**
[FontClearUnderline](/domino-c-api-docs/reference/Func/FontClearUnderline)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontSetUnderline](/domino-c-api-docs/reference/Func/FontSetUnderline)
---
