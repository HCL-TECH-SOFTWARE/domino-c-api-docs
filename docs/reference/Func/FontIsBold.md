##### Function : Font
##### FontIsBold - Returns TRUE if the specified FONTID has the BOLD attribute set, FALSE otherwise.
---
```
#include <fontid.h>
BOOL FontIsBold(

	FONTID  fontid);
```
**Description :**

Tests to see if the BOLD attribute is set in the specified FONTID.  Implemented 
as a macro:

#define FontIsBold(fontid) (((fontid) & ((DWORD) ISBOLD << FONT_STYLE_SHIFT)) 
!= 0)

**Parameters :**
Input :
fontid  -  The FONTID which is to be checked.

Output :
(routine)  -  TRUE if the BOLD attribute is set, FALSE otherwise



**See Also :**
[FONTID](/domino-c-api-docs/reference/Data/FONTID)
[FONTIDFIELDS](/domino-c-api-docs/reference/Data/FONTIDFIELDS)
[FontSetBold](/domino-c-api-docs/reference/Func/FontSetBold)
[FontClearBold](/domino-c-api-docs/reference/Func/FontClearBold)
---
