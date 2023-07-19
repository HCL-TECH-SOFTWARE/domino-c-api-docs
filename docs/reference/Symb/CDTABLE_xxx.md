##### Symbolic Value : Rich Text
##### CDTABLE_xxx - CDTABLEBEGIN Flags
---
```
#include <editods.h>
```

**Symbolic Values :**

	CDTABLE_AUTO_CELL_WIDTH	  -  Cell widths are calculated automatically. The table width is set to "Fit with margins" or "Fit to window". Further details are set in the Flags member of the CDPRETABLEBEGIN structure.

	CDTABLE_V4_BORDERS	  -  The table was created with R4 or later releases. The table contains width information that is not found in previous releases of Notes.

	CDTABLE_3D_BORDER_EMBOSS	  -  The table uses embossed cell borders (groove cell border style).

	CDTABLE_3D_BORDER_EXTRUDE	  -  If set, the table uses extruded cell borders (ridge cell border style).

	CDTABLE_BIDI_RTLTABLE	  -  The table reading order is right to left.

	CDTABLE_ALIGNED_RIGHT	  -  The table position is aligned to the right.

	CDTABLE_COLLAPSIBLE	  -  Show only one row at a time. Further details are set in the ViewType member of the CDPRETABLEBEGIN structure.

	CDTABLE_LEFTTOP	  -  Table Color Style is set to Left and Top.

	CDTABLE_TOP	  -  Table Color Style is set to Top.

	CDTABLE_LEFT	  -  Table Color Style is set to Left.

	CDTABLE_ALTERNATINGCOLS	  -  Table Color Style is set to Alternating Columns.

	CDTABLE_ALTERNATINGROWS	  -  Table Color Style is set to Alternating Rows.

	CDTABLE_RIGHTTOP	  -  Table Color Style is set to Right and Top.

	CDTABLE_RIGHT	  -  Table Color Style is set to Right

	CDTABLE_SOLID	  -  This flag is used as a bit mask. If all the bits in this mask are set, then the Table Color Style is set to Solid.

	CDTABLE_TEMPLATEBITS	  -  Bit mask for the various Table Color Styles.

	CDTABLE_ALIGNED_CENTER	  -  Table position is aligned in the center.

	CDTABLE_TEXTFLOWS	  -  Set text to flow from one cell to the next horizontally.


**Description :**

Flag values stored in the Flags field of the CDTABLEBEGIN record.


**See Also :**
[CDTABLEBEGIN](/domino-c-api-docs/reference/Data/CDTABLEBEGIN)
[CDPRETABLEBEGIN](/domino-c-api-docs/reference/Data/CDPRETABLEBEGIN)
[CDPRETABLE_xxx](/domino-c-api-docs/reference/Symb/CDPRETABLE_xxx)
[CDTABLEVIEWER_xxx](/domino-c-api-docs/reference/Symb/CDTABLEVIEWER_xxx)
---
