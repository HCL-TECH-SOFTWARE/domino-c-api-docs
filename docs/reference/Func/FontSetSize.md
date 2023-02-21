##### Function : Font
##### FontSetSize - Sets the FONTID's PointSize byte to the specified value.
---
```
#include <fontid.h>
FONTID FontSetSize(

	FONTID  fontid,
	DWORD  size);
```
**Description :**

Implemented as a macro:

#define FontSetSize(fontid,size) (((DWORD)(fontid) & 
~BYTEMASK(FONT_SIZE_SHIFT)) | ((DWORD)(size)<<FONT_SIZE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to set the PointSize byte.

size  -  The size (in points) to which  the FONTID's PointSize byte is to be set.

Output :
(routine)  -  The specified FONTID with the PointSize set to the specified value.



**See Also :**
[FontGetSize](/domino-c-api-docs/reference/Func/FontGetSize)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
---
