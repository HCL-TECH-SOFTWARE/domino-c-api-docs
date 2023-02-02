##### Function : Font
##### FontGetFaceID - Returns the value of the FONTID's Face byte.
---
##### #include <fontid.h>
BYTE **FontGetFaceID(**

	FONTID  fontid);
**Description :**
Returns the value of the FONTID's Face byte. This may be one of the standard 
type faces defined by FONT_FACE_xxx or a font ID resolved by a font table.  
Implemented as a macro:

#define FontGetFaceID(fontid) ((BYTE)(((fontid) >> FONT_FACE_SHIFT) & 0xff))
**Parameters :**
Input :
fontid  -  The FONTID from which to read the Face byte.

Output :
(routine)  -  The value of the FONTID's Face byte.


**See Also :**
[CDFONTTABLE](D:/md_files/CDFONTTABLE.md)
[FONTID](D:/md_files/FONTID.md)
[FONTIDFIELDS](D:/md_files/FONTIDFIELDS.md)
[FontSetFaceID](D:/md_files/FontSetFaceID.md)
[FONT_FACE_xxx](D:/md_files/FONT_FACE_xxx.md)
---
