##### Function : Font
##### FontClearEmboss - Turns off the EMBOSS attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontClearEmboss(

	FONTID  fontid);
```
**Description :**

This function turns off the EMBOSS attribute in the specified FONTID.  Text 
that has the EMBOSS attribute appears to be sticking out of the page.

Implemented as a macro:

#define FontClearEmboss(fontid) ((DWORD)(fontid) & ~(ISEMBOSS << 
FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to clear the EMBOSS attribute.

Output :
(routine)  -  The specified FONTID with the EMBOSS attribute turned off.



**See Also :**
[FontSetEmboss](/reference/Func/FontSetEmboss)
[FontIsEmboss](/reference/Func/FontIsEmboss)
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
---
