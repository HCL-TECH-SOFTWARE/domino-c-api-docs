##### Function : Font
##### FontClearBold - Turns off the BOLD attribute in the specified FONTID.
---
```
#include <fontid.h>
FONTID FontClearBold(

	FONTID  fontid);
```
**Description :**

This routine turns off the BOLD attribute in the specified FONTID.

Implemented as a macro:

#define FontClearBold(fontid) ((DWORD)(fontid) & ~(ISBOLD << FONT_STYLE_SHIFT))

**Parameters :**
Input :
fontid  -  The FONTID in which to clear the BOLD attribute.

Output :
(routine)  -  The specified FONTID with the BOLD attribute turned off.



**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontIsBold](/domino-c-api-docs/reference/Func/FontIsBold)
[FontSetBold](/domino-c-api-docs/reference/Func/FontSetBold)
---
