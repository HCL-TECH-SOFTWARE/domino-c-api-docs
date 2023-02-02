##### Function : Font
##### FontClearBold - Turns off the BOLD attribute in the specified FONTID.
---
##### #include <fontid.h>
FONTID **FontClearBold(**

	FONTID  fontid);
**Description :**
This routine turns off the BOLD attribute in the specified FONTID.

Implemented as a macro:

#define FontClearBold(fontid) ((DWORD)(fontid) & ~(ISBOLD << FONT_STYLE_SHIFT))
**Parameters :**
Input :
fontid  -  The FONTID in which to clear the BOLD attribute.

Output :
(routine)  -  The specified FONTID with the BOLD attribute turned off.


**See Also :**
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontIsBold](D:/md_files/FontIsBold.md)
[FontSetBold](D:/md_files/FontSetBold.md)
---
