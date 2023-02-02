##### Function : Font
##### FontIsSuperScript - Returns TRUE if the specified FONTID has the SUPERSCRIPT attribute set, FALSE otherwise.
---
##### #include <fontid.h>
BOOL **FontIsSuperScript(**

	FONTID  fontid);
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
[FontClearSuperScript](D:/md_files/FontClearSuperScript.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontSetSuperScript](D:/md_files/FontSetSuperScript.md)
---
