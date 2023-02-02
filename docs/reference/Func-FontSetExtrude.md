##### Function : Font
##### FontSetExtrude - Turns on the EXTRUDE attribute in the specified FONTID.
---
##### #include <fontid.h>
FONTID **FontSetExtrude(**

	FONTID  fontid);
**Description :**
This routine sets the EXTRUDE attribute in the specified FONTID.  Text that has 
the EXTRUDE attribute appears to be pushed into the page.

Implemented as a macro:

#define FontSetExtrude(fontid) ((DWORD)(fontid) | (ISEXTRUDE << 
FONT_STYLE_SHIFT))

The EMBOSS attribute and the EXTRUDE attribute are mutually exclusive.  When 
setting the EXTRUDE attribute, make sure the EMBOSS attribute is cleared.
**Parameters :**
Input :
fontid  -  The FONTID in which to set the EXTRUDE attribute.

Output :
(routine)  -  The specified FONTID with the EXTRUDE attribute turned on.


**See Also :**
[FontClearExtrude](D:/md_files/FontClearExtrude.md)
[FontIsExtrude](D:/md_files/FontIsExtrude.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
---
