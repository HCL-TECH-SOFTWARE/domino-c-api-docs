##### Function : Font
##### FontSetBold - Turns on the BOLD attribute in the specified FONTID.
---
##### #include <fontid.h>
FONTID **FontSetBold(**

	FONTID  fontid);
**Description :**
Turns on the BOLD attribute in the specified FONTID.  Implemented as a macro:

#define FontSetBold(fontid) ((DWORD)(fontid) | (ISBOLD << FONT_STYLE_SHIFT))
**Parameters :**
Input :
fontid  -  The FONTID in which to set the BOLD attribute.


Output :
(routine)  -  The specified FONTID with the BOLD attribute turned on.


**See Also :**
[FontClearBold](D:/md_files/FontClearBold.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontIsBold](D:/md_files/FontIsBold.md)
---
