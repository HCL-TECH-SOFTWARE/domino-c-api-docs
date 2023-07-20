##### Symbolic Value : Font
##### FONT_xxx_SHIFT - Symbolic definitions used in a call to BYTEMASK.
---
```
#include <fontid.h>
```

**Symbolic Values :**

	FONT_SIZE_SHIFT	  -  Create a mask for the PointSize byte in a FONTID.

	FONT_COLOR_SHIFT	  -  Create a mask for the Color byte in a FONTID.

	FONT_STYLE_SHIFT	  -  Create a mask for the Attrib byte in a FONTID.

	FONT_FACE_SHIFT	  -  Create a mask for the Face byte in a FONTID.


**Description :**

These symbolic definitions are used in calls to the function BYTEMASK to specify which byte in a DWORD is be masked off. These values are usually used in macros that access the bytes in a FONTID.


**See Also :**
[BYTEMASK](/domino-c-api-docs/reference/Func/BYTEMASK)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
---
