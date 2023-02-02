##### Function : Font
##### FontSetSuperScript - Turns on the SUPERSCRIPT attribute in the specified FONTID.
---
##### #include <fontid.h>
FONTID **FontSetSuperScript(**

	FONTID  fontid);
**Description :**
Implemented as a macro:

#define FontSetSuperScript(fontid) ((DWORD)(fontid) | (ISSUPER << 
FONT_STYLE_SHIFT))
**Parameters :**
Input :
fontid  -  The FONTID in which to set the SUPERSCRIPT attribute.

Output :
(routine)  -  The specified FONTID with the SUPERSCRIPT attribute turned on.


**See Also :**
[FontClearSuperScript](D:/md_files/FontClearSuperScript.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontIsSuperScript](D:/md_files/FontIsSuperScript.md)
---
