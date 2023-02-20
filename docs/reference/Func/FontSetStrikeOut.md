##### Function : Font
##### FontSetStrikeOut - Turns on the STRIKEOUT attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontSetStrikeOut(

	FONTID  fontid);
```
**Description :**

Implemented as a macro:

#define FontSetStrikeOut(fontid) ((DWORD)(fontid) | (ISSTRIKEOUT << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to set the STRIKEOUT attribute.

Output :
(routine)  -  The specified FONTID with the STRIKEOUT attribute turned on.



**See Also :**
[FontClearStrikeOut](/reference/Func/FontClearStrikeOut)
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
[FontIsStrikeOut](/reference/Func/FontIsStrikeOut)
---
