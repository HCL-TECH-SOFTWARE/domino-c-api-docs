##### Function : Font
##### FontIsItalic - Returns TRUE if the specified FONTID has the ITALIC attribute set, FALSE otherwise.
---
##### #include <fontid.h>
BOOL **FontIsItalic(**

	FONTID  fontid);
**Description :**
Tests to see if the ITALIC attribute is set in the specified FONTID.  
Implemented as a macro:

#define FontIsItalic(fontid) (((fontid) & ((DWORD) ISITALIC << 
FONT_STYLE_SHIFT)) != 0)
**Parameters :**
Input :
fontid  -  The FONTID which is to be checked.


Output :
(routine)  -  TRUE if the ITALIC attribute is set, FALSE otherwise


**See Also :**
[FontClearItalic](D:/md_files/FontClearItalic.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontSetItalic](D:/md_files/FontSetItalic.md)
---
