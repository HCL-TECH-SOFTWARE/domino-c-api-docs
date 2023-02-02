##### Function : Font
##### FontClearEffect - Turns off the EFFECT attribute in the specified FONTID.
---
##### #include <fontid.h>
FONTID **FontClearEffect(**

	FONTID  fontid);
**Description :**
This function turns off the EFFECT attribute in the specified FONTID.  The 
EFFECT attribute, if set, means that the text has a special effect style such 
as shadowed, embossed, or extruded text.

Implemented as a macro:

#define FontClearEffect(fontid) ((DWORD)(fontid) & ~((ISEMBOSS|ISEXTRUDE) << 
FONT_STYLE_SHIFT))
**Parameters :**
Input :
fontid  -  The FONTID in which to clear the EFFECT attribute.

Output :
(routine)  -  The specified FONTID with the EFFECT attribute turned off.


**See Also :**
[FontIsEffect](D:/md_files/FontIsEffect.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
---
