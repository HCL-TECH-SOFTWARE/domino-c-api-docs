##### Function : Font
##### FontClearUnderline - Turns off the UNDERLINE attribute in the specified FONTID
---
```
#include <fontid.h>
FONTID FontClearUnderline(

	FONTID  fontid);
```
**Description :**

Implemented as a macro:

#define FontClearUnderline(fontid) ((DWORD)(fontid) & ~(ISUNDERLINE << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to clear the UNDERLINE attribute.

Output :
(routine)  -  The specified FONTID with the UNDERLINE attribute turned off.



**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontIsUnderline](/domino-c-api-docs/reference/Func/FontIsUnderline)
[FontSetUnderline](/domino-c-api-docs/reference/Func/FontSetUnderline)
---
