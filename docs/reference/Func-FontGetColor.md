##### Function : Font
##### FontGetColor - Returns the value of the FONTID's Color byte.
---
##### #include <fontid.h>
BYTE **FontGetColor(**

	FONTID  fontid);
**Description :**
Returns the value of the FONTID's Color byte.  The value returned will be one 
of the values defined by NOTES_COLOR_xxx.  Implemented as a macro:

#define FontGetColor(fontid) ((BYTE)(((fontid) >> FONT_COLOR_SHIFT) & 0xff))
**Parameters :**
Input :
fontid  -  The FONTID from which to read the Color byte.

Output :
(routine)  -  The value of the FONTID's color byte.


**See Also :**
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontSetColor](D:/md_files/FontSetColor.md)
[NOTES_COLOR_xxx](D:/md_files/NOTES_COLOR_xxx.md)
---
