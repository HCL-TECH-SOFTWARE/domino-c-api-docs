##### Symbolic Value : Composite Data
##### BARREC_xxx - CDBAR - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	BARREC_DISABLED_FOR_NON_EDITORS	  -  Section can be expanded only if the current user has editing privileges.

	BARREC_EXPANDED	  -  Section is expanded.

	BARREC_PREVIEW	  -  The bar is preview only.

	BARREC_BORDER_INVISIBLE	  -  Border is not visible around section title.

	BARREC_ISFORMULA	  -  Bar caption is a formula.

	BARREC_HIDE_EXPANDED	  -  Caption is hidden when bar is expanded.

	BARREC_INTENDED	  -  Whether the user can edit this bar or not.

	BARREC_HAS_COLOR	  -  The bar has an explicit color reference.

	BARREC_BORDER_MASK	  -  Mask used for getting and setting the border type.

	BARREC_BORDER_SHADOW	  -  Draw a shadow around the border of the bar.

	BARREC_BORDER_NONE	  -  No default border style.

	BARREC_BORDER_SINGLE	  -  Bar is single thickness.

	BARREC_BORDER_DOUBLE	  -  Bar is double thickness.

	BARREC_BORDER_TRIPLE	  -  Bar is triple thickness.

	BARREC_BORDER_TWOLINE	  -  Bar is two lines.

	BARREC_BORDER_WINDOWCAPTION	  -  Shaded box is visible around section title. Open and close is indicated by icon on right of section.

	BARREC_BORDER_OTHER	  -  Used to create tab or diagonal sections. See Description below for more information.

	BARREC_BORDER_GRADIENT	  -  Box is visible around section title with shading blended to match the background.

	BARREC_BORDER_TAB	  -  Section is indicated by a tab.

	BARREC_BORDER_DIAG	  -  Section is indicated by a tab with a diagonal border.

	BARREC_INDENTED	  -  Unused

	BARREC_ODS_MASK	  -  Used to set bits that don't need to be stored on disk to 0.


**Description :**

On-disk flags for CDBAR (Collapsible Sections). For collapsible sections indicated by a tab or a tab with a diagonal border, the CDBAR record (with its Flags member set to BARREC_BORDER_OTHER) is followed by a CDDATAFLAGS structure with its Flags member set to BARREC_DATA_BORDER_TAB (for tab) or BARREC_DATA_BORDER_DIAG (for diagonal).


**See Also :**
[CDBAR](/domino-c-api-docs/reference/Data/CDBAR)
[CDDATAFLAGS](/domino-c-api-docs/reference/Data/CDDATAFLAGS)
---
