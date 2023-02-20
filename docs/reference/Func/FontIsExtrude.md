##### Function : Font
##### FontIsExtrude - Returns TRUE if the specified FONTID has the EXTRUDE attribute set, FALSE otherwise.
---
```
#include <fontid.h>
BOOL FontIsExtrude(

	FONTID  fontid);
```
**Description :**

This routine tests if the EXTRUDE attribute is set in the specified FONTID.  
Text that has the EXTRUDE attribute appears to be pushed into the page.

Implemented as a macro:

#define FontIsExtrude(fontid) (((fontid) & ((DWORD) ISEXTRUDE << 
FONT_STYLE_SHIFT)) == ((DWORD) ISEXTRUDE << FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID which is to be checked for the EXTRUDE attribute.

Output :
(routine)  -  TRUE if the EXTRUDE attribute is set, FALSE otherwise



**See Also :**
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
[FontClearExtrude](/reference/Func/FontClearExtrude)
[FontSetExtrude](/reference/Func/FontSetExtrude)
---
