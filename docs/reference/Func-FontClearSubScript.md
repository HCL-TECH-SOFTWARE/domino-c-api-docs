##### Function : Font
##### FontClearSubScript - Turns off the SUBSCRIPT attribute in the specified FONTID
---
##### #include <fontid.h>
FONTID **FontClearSubScript(**

	FONTID  fontid);
**Description :**
Implemented as a macro:

#define FontClearSubScript(fontid) ((DWORD)(fontid) & ~(ISSUB << 
FONT_STYLE_SHIFT))
**Parameters :**
Input :
fontid  -  The FONTID in which to clear the SUBSCRIPT attribute

Output :
(routine)  -  The specified FONTID with the SUBSCRIPT attribute turned off.


**See Also :**
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontIsSubScript](D:/md_files/FontIsSubScript.md)
[FontSetSubScript](D:/md_files/FontSetSubScript.md)
---
