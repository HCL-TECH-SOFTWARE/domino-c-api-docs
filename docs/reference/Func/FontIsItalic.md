##### Function : Font
##### FontIsItalic - Returns TRUE if the specified FONTID has the ITALIC attribute set, FALSE otherwise.
---
```
#include <fontid.h>
BOOL FontIsItalic(

	FONTID  fontid);
```
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
[FontClearItalic](/reference/Func/FontClearItalic)
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
[FontSetItalic](/reference/Func/FontSetItalic)
---
