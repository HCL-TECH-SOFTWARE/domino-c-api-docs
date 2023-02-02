##### Function : Font
##### FontSetShadow - Turns on the SHADOW attribute in the specified FONTID.
---
##### #include <fontid.h>
FONTID **FontSetShadow(**

	FONTID  fontid);
**Description :**
This routine sets the SHADOW attribute in the specified FONTID.

Implemented as a macro:

#define FontSetShadow(fontid) ((DWORD)(fontid) | (ISSHADOW << 
FONT_STYLE_SHIFT))
**Parameters :**
Input :
fontid  -  The FONTID in which to set the SHADOW attribute.

Output :
(routine)  -  The specified FONTID with the SHADOW attribute turned on.


**See Also :**
[FontClearShadow](D:/md_files/FontClearShadow.md)
[FontGetShadowOffset](D:/md_files/FontGetShadowOffset.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
---
