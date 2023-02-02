##### Function : Font
##### FontClearSuperScript - Turns off the SUPERSCRIPT attribute in the specified FONTID
---
##### #include <fontid.h>
FONTID **FontClearSuperScript(**

	FONTID  fontid);
**Description :**
Implemented as a macro:

#define FontClearSuperScript(fontid) ((DWORD)(fontid) & ~(ISSUPER << 
FONT_STYLE_SHIFT))
**Parameters :**
Input :
fontid  -  The FONTID in which to clear the SUPERSCRIPT attribute

Output :
(routine)  -  The specified FONTID with the SUPERSCRIPT attribute turned off


**See Also :**
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontIsSuperScript](D:/md_files/FontIsSuperScript.md)
[FontSetSuperScript](D:/md_files/FontSetSuperScript.md)
---
