##### Function : Font
##### FontSetItalic - Turns on the ITALIC attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontSetItalic(

	FONTID  fontid);
```
**Description :**

This routine sets the ITALIC attribute in the specified FONTID.

Implemented as a macro:

#define FontSetItalic(fontid) ((DWORD)(fontid) | (ISITALIC << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to set the ITALIC attribute.



Output :
(routine)  -  The specified FONTID with the ITALIC attribute turned on.



**See Also :**
[FontClearItalic](/domino-c-api-docs/reference/Func/FontClearItalic)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontIsItalic](/domino-c-api-docs/reference/Func/FontIsItalic)
---
