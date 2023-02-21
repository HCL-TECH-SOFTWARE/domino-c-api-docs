##### Function : Font
##### FontClearStrikeOut - Turns off the STRIKEOUT attribute in the specified FONTID
---
```
#include <fontid.h>
FONTID FontClearStrikeOut(

	FONTID  fontid);
```
**Description :**

Implemented as a macro:

#define FontClearStrikeOut(fontid) ((DWORD)(fontid) & ~(ISSTRIKEOUT << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to clear the STRIKEOUT attribute.

Output :
(routine)  -  The specified FONTID with the STRIKEOUT attribute turned off.



**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontIsStrikeOut](/domino-c-api-docs/reference/Func/FontIsStrikeOut)
[FontSetStrikeOut](/domino-c-api-docs/reference/Func/FontSetStrikeOut)
---
