##### Function : Font
##### FontClearItalic - Turns off the ITALIC attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontClearItalic(

	FONTID  fontid);
```
**Description :**

This function turns off the ITALIC attribute in the specified FONTID.

Implemented as a macro:

#define FontClearItalic(fontid) ((DWORD)(fontid) & ~(ISITALIC << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to clear the ITALIC attribute.


Output :
(routine)  -  The specified FONTID with the ITALIC attribute turned off.



**See Also :**
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
[FontIsItalic](/reference/Func/FontIsItalic)
[FontSetItalic](/reference/Func/FontSetItalic)
---
