##### Function : Font
##### FontIsPlain - Returns TRUE if none of the style attibutes (BOLD, ITALIC, etc.) are set in the specified FONTID, FALSE otherwise.
---
```
#include <fontid.h>
BOOL FontIsPlain(

	FONTID  fontid);
```
**Description :**

Tests to see if none of the bits in the Attrib byte of the specified FONTID 
data structure are set.  Implemented as a macro:

#define FontIsPlain(fontid) (FontGetStyle(fontid) == 0)

**Parameters :**
Input :
fontid  -  The FONTID in which the Attrib byte is to be checked.

Output :
(routine)  -  TRUE if none of the style attributes are set, False otherwise



**See Also :**
[FONTID](/reference/Data/FONTID)
[FONTIDFIELDS](/reference/Data/FONTIDFIELDS)
[FontSetPlain](/reference/Func/FontSetPlain)
---
