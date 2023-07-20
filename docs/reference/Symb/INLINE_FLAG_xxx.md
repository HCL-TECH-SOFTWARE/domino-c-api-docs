##### Symbolic Value : Composite Data
##### INLINE_FLAG_xxx - Values for the dwFlags member of CDINLINE. 
---
```
#include <editods.h>
```

**Symbolic Values :**

	INLINE_FLAG_UNKNOWN	  -  If flag is set, resource is of unknown type.

	INLINE_FLAG_SCRIPT_LIB	  -  If flag is set, resource is a JavaScript library.

	INLINE_FLAG_STYLE_SHEET	  -  If flag is set, resource is a style sheet.

	INLINE_FLAG_HTML	  -  If flag is set, resource is HTML

	INLINE_FLAG_HTMLFILERES	  -  If flag is set, resource is an HTML file.

	INLINE_FLAG_TYPES_MASK	  -  Mask for the INLINE flags.


**Description :**

These flags are values for the dwFlags member of CDINLINE.  A CDINLINE record may be preceded by a CDBEGINRECORD and followed by a CDRESOURCE and then a CDENDRECORD.  


**See Also :**
[CDINLINE](/domino-c-api-docs/reference/Data/CDINLINE)
[CDRESOURCE](/domino-c-api-docs/reference/Data/CDRESOURCE)
---
