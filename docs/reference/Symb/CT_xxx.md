##### Symbolic Value : Rich Text
##### CT_xxx - Miscellaneous color table defines and macros.
---
```
#include <editods.h>
```

**Symbolic Values :**

	CT_ENTRY_SIZE	  -  Always 3 bytes, packed.

	CT_REDVALUE(x)	  -  (x[CT_RED_OFFSET])

	CT_GREENVALUE(x)	  -  (x[CT_GREEN_OFFSET])

	CT_BLUEVALUE(x)	  -  (x[CT_BLUE_OFFSET])

	CT_NEXT(x)	  -  (x+=CT_ENTRY_SIZE)

	CT_ENTRY_PTR(x,ElmNum)	  -  (&x[CT_ENTRY_SIZE*ElmNum])


**Description :**

These values and macros can be used for color table entries of the CDCOLORTABLE and CDPATTERNTABLE structures.  


**See Also :**
[CDBITMAPHEADER](/domino-c-api-docs/reference/Data/CDBITMAPHEADER)
[CDCOLORTABLE](/domino-c-api-docs/reference/Data/CDCOLORTABLE)
[CDPATTERNTABLE](/domino-c-api-docs/reference/Data/CDPATTERNTABLE)
[CT_xxx_OFFSET](/domino-c-api-docs/reference/Symb/CT_xxx_OFFSET)
---
