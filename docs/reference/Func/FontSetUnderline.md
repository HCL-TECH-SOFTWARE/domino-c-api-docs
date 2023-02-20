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
[FontClearUnderline](/reference/Func/FontClearUnderline)
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
[FontIsUnderline](/reference/Func/FontIsUnderline)
---
