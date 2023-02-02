##### Function : Font
##### FontGetShadowOffset - Returns the offset of the shadow relative to the text.
---
##### #include <fontid.h>
BYTE **FontGetShadowOffset(**

	FONTID  fontid);
**Description :**
This routine returns the offset of the shadow.  Shadowed text is a two pass 
process where the text is first drawn with the shadow color at an offset from 
the actual text.  This offset is currently a fixed fraction of the font size.  
The actual text is then drawn.

Implemented as a macro:

#define FontGetShadowOffset(fontid) 
(BYTE)(FontGetSize(fontid)/(BYTE)FONT_SHADOW_VALUE + 1)
**Parameters :**
Input :
fontid  -  The FONTID in which to compute the SHADOW offset.

Output :
(routine)  -  Offset, in points, from the text's position which specifies where the shadow to the text is drawn.


**See Also :**
[FontClearShadow](D:/md_files/FontClearShadow.md)
[FontSetShadow](D:/md_files/FontSetShadow.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
---
