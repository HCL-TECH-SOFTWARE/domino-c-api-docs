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
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
[FontIsStrikeOut](/reference/Func/FontIsStrikeOut)
[FontSetStrikeOut](/reference/Func/FontSetStrikeOut)
---
