##### Symbolic Value : Composite Data
##### BARREC_AUTO_xxx - CDBAR - Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	BARREC_AUTO_EXP_READ	  -  Expand when reading.

	BARREC_AUTO_EXP_PRE	  -  Expand when previewing.

	BARREC_AUTO_EXP_EDIT	  -  Expand when editing.

	BARREC_AUTO_EXP_PRINT	  -  Expand when printing.

	BARREC_AUTO_EXP_MASK	  -  Mask for the auto expand flags.

	BARREC_AUTO_COL_READ	  -  Collapse when reading.

	BARREC_AUTO_COL_PRE	  -  Collapse when previewing.

	BARREC_AUTO_COL_EDIT	  -  Collapse when editing.

	BARREC_AUTO_COL_PRINT	  -  Collapse when printing.

	BARREC_AUTO_COL_MASK	  -  Mask for the auto collapse flags.

	BARREC_AUTO_PRE_MASK	  -  Used to determine whether it is expanded or collapsed for preview mode.

	BARREC_AUTO_READ_MASK	  -  Used to determine whether it is expanded or collapsed for read mode.

	BARREC_AUTO_EDIT_MASK	  -  Used to determine whether it is expanded or collapsed for preview mode.

	BARREC_AUTO_PRINT_MASK	  -  Used to determine whether it is expanded or collapsed for preview mode.

	BARREC_AUTO_ED_SHIFT	  -  Used to shift the flags 12 bits to check the editor flags.

	BARREC_AUTO_ED_EXP_READ	  -  Used in the BARREC_AUTO_READ_MASK.

	BARREC_AUTO_ED_EXP_PRE	  -  Used in the BARREC_AUTO_PRE_MASK.

	BARREC_AUTO_ED_EXP_EDIT	  -  Used in the BARREC_AUTO_EDIT_MASK.

	BARREC_AUTO_ED_EXP_PRINT	  -  Used in the BARREC_AUTO_PRINT_MASK.

	BARREC_AUTO_ED_EXP_MASK	  -  Unused

	BARREC_AUTO_ED_COL_READ	  -  Used in the BARREC_AUTO_READ_MASK.

	BARREC_AUTO_ED_COL_PRE	  -  Used in the BARREC_AUTO_PRE_MASK.

	BARREC_AUTO_ED_COL_EDIT	  -  Used in the BARREC_AUTO_EDIT_MASK.

	BARREC_AUTO_ED_COL_PRINT	  -  Used in the BARREC_AUTO_PRINT_MASK.

	BARREC_AUTO_ED_COL_MASK	  -  Unused

	BARREC_AUTO_ED_PRE_MASK	  -  Checks if either expanded or collapsed has been set for preview mode.

	BARREC_AUTO_ED_READ_MASK	  -  Checks if either expanded or collapsed has been set for read mode.

	BARREC_AUTO_ED_EDIT_MASK	  -  Checks if either expanded or collapsed has been set for edit mode.

	BARREC_AUTO_ED_PRINT_MASK	  -  Checks if either expanded or collapsed has been set for print mode.


**Description :**

On-disk flags for CDBAR (Collapsible Sections)


**See Also :**
[CDBAR](/domino-c-api-docs/reference/Data/CDBAR)
---
