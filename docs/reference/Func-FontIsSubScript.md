##### Function : Font
##### FontIsSubScript - Returns TRUE if the specified FONTID has the SUBSCRIPT attribute set, FALSE otherwise.
---
##### #include <fontid.h>
BOOL **FontIsSubScript(**

	FONTID  fontid);
**Description :**
Tests to see if the SUBSCRIPT attribute is set in the specified FONTID.  
Implemented as a macro:

#define FontIsSubScript(fontid) (((fontid) & ((DWORD)(ISEFFECT|ISSUB) << 
FONT_STYLE_SHIFT)) == (DWORD)(ISSUB << FONT_STYLE_SHIFT))
**Parameters :**
Input :
fontid  -  The FONTID which is to be checked.

Output :
(routine)  -  TRUE if the SUBSCRIPT attribute is set, FALSE otherwise.


**See Also :**
[FontClearSubScript](D:/md_files/FontClearSubScript.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontSetSubScript](D:/md_files/FontSetSubScript.md)
---
