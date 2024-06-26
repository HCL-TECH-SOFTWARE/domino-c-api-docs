##### Function : Font
##### FontIsStrikeOut - Returns TRUE if the specified FONTID has the STRIKEOUT attribute set, FALSE otherwise.
---
```
#include <fontid.h>
BOOL FontIsStrikeOut(

	FONTID  fontid);
```
**Description :**

Tests to see if the STRIKEOUT attribute is set in the specified FONTID.  
Implemented as a macro:

#define FontIsStrikeOut(fontid) (((fontid) & ((DWORD) ISSTRIKEOUT << 
FONT_STYLE_SHIFT)) != 0)

**Parameters :**
Input :
fontid  -  The FONTID which is to be checked.

Output :
(routine)  -  TRUE if the STRIKEOUT attribute is set, FALSE otherwise.



**See Also :**
[FontClearStrikeOut](/domino-c-api-docs/reference/Func/FontClearStrikeOut)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontSetStrikeOut](/domino-c-api-docs/reference/Func/FontSetStrikeOut)
---
