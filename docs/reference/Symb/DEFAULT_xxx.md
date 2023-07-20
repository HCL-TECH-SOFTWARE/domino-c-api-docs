##### Symbolic Value : Rich Text
##### DEFAULT_xxx - Various default settings for Paragraph Attribute Blocks, table cells, and layout regions.
---
```
#include <editdflt.h>
```

**Symbolic Values :**

	DEFAULT_JUSTIFICATION	  -  JUSTIFY_LEFT

	DEFAULT_LINE_SPACING	  -  0

	DEFAULT_ABOVE_PAR_SPACING	  -  0

	DEFAULT_BELOW_PAR_SPACING	  -  0

	DEFAULT_LEFT_MARGIN	  -  ONEINCH

	DEFAULT_FIRST_LEFT_MARGIN	  -  DEFAULT_LEFT_MARGIN

	DEFAULT_RIGHT_MARGIN	  -  0

Note: Right Margin = "0" means [DEFAULT_RIGHT_GUTTER] inches from right edge of paper, regardless of paper width.

	DEFAULT_RIGHT_GUTTER	  -  ONEINCH

	DEFAULT_PAGINATION	  -  0

Note: Tabs are relative to the absolute left edge of the paper.

	DEFAULT_FLAGS2	  -  0

	DEFAULT_MARGIN_STYLE	  -  PABFLAG2_LM_OFFSET | PABFLAG2_RM_OFFSET

	DEFAULT_TABS	  -  0

	DEFAULT_TAB_INTERVAL	  -  (ONEINCH/2)

	DEFAULT_TABLE_HCELLSPACE	  -  0

	DEFAULT_TABLE_VCELLSPACE	  -  0

	DEFAULT_LAYOUT_LEFT	  -  DEFAULT_LEFT_MARGIN

	DEFAULT_LAYOUT_WIDTH	  -  (ONEINCH * 6)

	DEFAULT_LAYOUT_HEIGHT	  -  (3 * ONEINCH / 2)

	DEFAULT_LAYOUT_ELEM_WIDTH	  -  (4 * ONEINCH / 3) /* 1.333 inch */

	DEFAULT_LAYOUT_ELEM_HEIGHT	  -  (ONEINCH / 5)


**Description :**

Various default settings for Paragraph Attribute Blocks, table cells, and layout regions.


**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
[CDTABLEBEGIN](/domino-c-api-docs/reference/Data/CDTABLEBEGIN)
[ELEMENTHEADER](/domino-c-api-docs/reference/Data/ELEMENTHEADER)
---
