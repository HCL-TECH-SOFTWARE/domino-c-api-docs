##### Function : Font
##### FontSetFaceID - Sets the FONTID's Face byte to the typeface specified in the faceid argument.
---
```
#include <fontid.h>
FONTID FontSetFaceID(

	FONTID  fontid,
	BYTE  faceid);
```
**Description :**

Sets the FONTID's Face byte to the typeface specified in the faceid argument. 
The faceid argument should be one of the values defined by FONT_FACE_xxx.  
Implemented as a macro:

#define FontSetFaceID(fontid,faceid) (((DWORD)(fontid) & 
~BYTEMASK(FONT_FACE_SHIFT)) | ((DWORD)(faceid)<<FONT_FACE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID  in which the Face byte is to be set.

faceid  -  The typeface to which the Face byte is to be set.

Output :
(routine)  -  The specified FONTID with the Face byte set appropriately.



**See Also :**
[FontGetFaceID](/domino-c-api-docs/reference/Func/FontGetFaceID)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FONT_FACE_xxx](/domino-c-api-docs/reference/Symb/FONT_FACE_xxx)
---
