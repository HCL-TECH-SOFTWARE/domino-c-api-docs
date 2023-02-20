##### Function : Font
##### FontIsSuperScript - Returns TRUE if the specified FONTID has the SUPERSCRIPT attribute set, FALSE otherwise.
---
```
#include <fontid.h>
BOOL FontIsSuperScript(

	FONTID  fontid);
```
**Description :**

Tests to see if the SUPERSCRIPT attribute is set in the specified FONTID.  
Implemented as a macro:

#define FontIsSuperScript(fontid) (((fontid) & ((DWORD)(ISEFFECT|ISSUPER) << 
FONT_STYLE_SHIFT)) == (DWORD)(ISSUPER << FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID which is to be checked.

Output :
(routine)  -  TRUE if the SUPERSCRIPT attribute is set, FALSE otherwise.



**See Also :**
[FontClearSuperScript](/reference/Func/FontClearSuperScript)
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
[FontSetSuperScript](/reference/Func/FontSetSuperScript)
---
