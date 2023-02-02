##### Function : Font
##### FontClearShadow - Turns off the SHADOW attribute in the specified FONTID.
---
##### #include <fontid.h>
FONTID **FontClearShadow(**

	FONTID  fontid);
**Description :**
This routine turns off the SHADOW attribute in the specified FONTID.

Implemented as a macro:

#define FontClearShadow(fontid) ((DWORD)(fontid) & ~(ISSHADOW << 
FONT_STYLE_SHIFT))
**Parameters :**
Input :
fontid  -  The FONTID in which to clear the SHADOW attribute.

Output :
(routine)  -  The specified FONTID with the SHADOW attribute turned off.


**See Also :**
[FontSetShadow](D:/md_files/FontSetShadow.md)
[FontGetShadowOffset](D:/md_files/FontGetShadowOffset.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FONTID](D:/md_files/FONTID.md)
---
