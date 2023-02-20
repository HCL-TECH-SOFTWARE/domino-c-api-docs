##### Function : Font
##### FontGetStyle - Returns the value of FONTID's Attrib byte.
---
```
#include <fontid.h>
BYTE FontGetStyle(

	FONTID  fontid);
```
**Description :**

Returns the value of the FONTID's Attrib byte, which defines the font's style 
characteristics (BOLD, ITALIC, etc.). Implemented as a macro:

#define FontGetStyle(fontid) ((BYTE)(((fontid) >> FONT_STYLE_SHIFT) & 0xff))

**Parameters :**
Input :
fontid  -  The FONTID from which to read the Attrib byte.

Output :
(routine)  -  The value of the FONTID's Attrib byte.



**See Also :**
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
[FontSetStyle](/reference/Func/FontSetStyle)
---
