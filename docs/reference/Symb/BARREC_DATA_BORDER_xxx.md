##### Symbolic Value : Composite Data
##### BARREC_DATA_BORDER_xxx - CDDATAFLAGS - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	BARREC_DATA_BORDER_MASK	  -  Mask used for getting and setting the data border type.

	BARREC_DATA_BORDER_GRADIENT	  -  Box is visible around section title with shading blended to match the background.

	BARREC_DATA_BORDER_TAB	  -  Section is indicated by a tab.

	BARREC_DATA_BORDER_DIAG	  -  Section is indicated by a tab with a diagonal border.


**Description :**

On-disk flags for CDDATAFLAGS. For collapsible sections indicated by a tab or a tab with a diagonal border, the CDBAR record (with its Flags member set to BARREC_BORDER_OTHER) is followed by a CDDATAFLAGS structure with its Flags member set to BARREC_DATA_BORDER_TAB (for tab) or BARREC_DATA_BORDER_DIAG (for diagonal).


**See Also :**
[CDDATAFLAGS](/domino-c-api-docs/reference/Data/CDDATAFLAGS)
---
