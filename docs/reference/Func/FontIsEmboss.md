##### Function : Font
##### FontIsEmboss - Returns TRUE if the specified FONTID has the EMBOSS attribute set, FALSE otherwise.
---
```
#include <editods.h>
BOOL FontIsEmboss(

	FONTID  fontid);
```
**Description :**

This routine tests if the EMBOSS attribute is set in the specified FONTID.  
Text that has the EMBOSS attribute appears to be sticking out of the page.

Implemented as a macro:

#define FontIsEmboss(fontid) (((fontid) & ((DWORD) ISEMBOSS << 
FONT_STYLE_SHIFT)) == ((DWORD) ISEMBOSS << FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID which is to be checked.

Output :
(routine)  -  TRUE if the EMBOSS attribute is set, FALSE otherwise



**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontClearEmboss](/domino-c-api-docs/reference/Func/FontClearEmboss)
[FontSetEmboss](/domino-c-api-docs/reference/Func/FontSetEmboss)
---
