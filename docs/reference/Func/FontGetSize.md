##### Function : Font
##### FontGetSize - Returns the size (in points) of the font.
---
```
#include <fontid.h>
BYTE FontGetSize(

	FONTID  fontid);
```
**Description :**

Returns the value of the FONTID's PointSize byte, which is the size of the font 
in points.  Implemented as a macro:

#define FontGetSize(fontid) ((BYTE)(((fontid) >> FONT_SIZE_SHIFT) & 0xff))

**Parameters :**
Input :
fontid  -  The FONTID from which to read the PointSize byte.

Output :
(routine)  -  The value of the FONTID's PointSize byte.



**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontSetSize](/domino-c-api-docs/reference/Func/FontSetSize)
---
