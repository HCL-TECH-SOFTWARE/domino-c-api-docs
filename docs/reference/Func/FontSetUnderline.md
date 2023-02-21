##### Function : Font
##### FontSetUnderline - Turns on the UNDERLINE attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontSetUnderline(

	FONTID  fontid);
```
**Description :**

Implemented as a macro:

#define FontSetUnderline(fontid) ((DWORD)(fontid) | (ISUNDERLINE << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to set the UNDERLINE attribute.

Output :
(routine)  -  The specified FONTID with the UNDERLINE attribute turned on.



**See Also :**
[FontClearUnderline](/domino-c-api-docs/reference/Func/FontClearUnderline)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontIsUnderline](/domino-c-api-docs/reference/Func/FontIsUnderline)
---
