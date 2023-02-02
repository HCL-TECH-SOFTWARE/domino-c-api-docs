##### Function : Font
##### FontSetColor - Sets the FONTID's Color byte to the color specified in the colorid argument.
---
##### #include <fontid.h>
FONTID **FontSetColor(**

	FONTID  fontid,
	BYTE  colorid);
**Description :**
Sets the FONTID's Color byte to the color specified in the colorid argument. 
The colorid argument should be one of the values defined by NOTES_COLOR_xxx.  
Implemented as a macro:

#define FontSetColor(fontid,colorid) (((DWORD)(fontid) & 
~BYTEMASK(FONT_COLOR_SHIFT)) | ((DWORD)(colorid)<<FONT_COLOR_SHIFT))
**Parameters :**
Input :
fontid  -  The FONTID in which the Color byte is to be set.

colorid  -  The symbolic value defined in NOTES_COLOR_xxx for the desired color.

Output :
(routine)  -  The specified FONTID with the Color byte set appropriately.


**See Also :**
[FontGetColor](D:/md_files/FontGetColor.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontSetColor](D:/md_files/FontSetColor.md)
[NOTES_COLOR_xxx](D:/md_files/NOTES_COLOR_xxx.md)
---
