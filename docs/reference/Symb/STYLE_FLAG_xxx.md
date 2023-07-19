##### Symbolic Value : Rich Text
##### STYLE_FLAG_xxx - CDSTYLENAME - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	STYLE_FLAG_FONTID	  -  A FONTID follows the CDSTYLENAME structure. The font is included in the style.

	STYLE_FLAG_INCYCLE	  -  This style is included in the Cycle Key [F11]. The style is available when you press F11 to cyle through the named styles

	STYLE_FLAG_PERMANENT	  -  A user name follows the CDSTYLENAME structure. If STYLE_FLAG_FONTID is also set, the CDSTYLENAME structure is followed by the FONTID which is then followed by the user name. The style is available for all documents.


**Description :**

Optional values for the Flags member of the CDSTYLENAME structure.


**See Also :**
[CDSTYLENAME](/domino-c-api-docs/reference/Data/CDSTYLENAME)
---
