##### Function : Font
##### FontSetBold - Turns on the BOLD attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontSetBold(

	FONTID  fontid);
```
**Description :**

Turns on the BOLD attribute in the specified FONTID.  Implemented as a macro:

#define FontSetBold(fontid) ((DWORD)(fontid) | (ISBOLD << FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to set the BOLD attribute.


Output :
(routine)  -  The specified FONTID with the BOLD attribute turned on.



**See Also :**
[FontClearBold](/domino-c-api-docs/reference/Func/FontClearBold)
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontIsBold](/domino-c-api-docs/reference/Func/FontIsBold)
---
