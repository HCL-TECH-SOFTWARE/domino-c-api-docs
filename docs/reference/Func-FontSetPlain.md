##### Function : Font
##### FontSetPlain - Turns off all of the style attributes (BOLD, ITALIC, etc.) in the specified FONTID.
---
##### #include <fontid.h>
FONTID **FontSetPlain(**

	FONTID  fontid);
**Description :**
Turns off all of the style attributes (BOLD, ITALIC, etc.) in the specified 
FONTID by setting the Attribute byte to zero.  Implemented as a macro:

#define FontSetPlain(fontid) (FontSetStyle(fontid,0))
**Parameters :**
Input :
fontid  -  The FONTID in which to clear all of the style attributes.

Output :
(routine)  -  The specified FONTID with all of the style attributes turned off.


**See Also :**
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontIsPlain](D:/md_files/FontIsPlain.md)
---
