##### Symbolic Value : Rich Text
##### CDPRETABLE_xxx - Flag defintions to CDPRETABLEBEGIN.
---
```
#include <editods.h>
```

**Symbolic Values :**

	CDPRETABLE_AUTO_CELL_WIDTH	  -  Cell widths are calculated automatically. If CDPRETABLE_WIDTHSAMEASWINDOW is not also set, the table width is set to "Fit with margins."

	CDPRETABLE_DONTWRAP	  -  Wrap text around the table.

	CDPRETABLE_DROPSHADOW	  -  Border effect is set to "Drop shadow."

	CDPRETABLE_FIELDDRIVEN	  -  Which row to display is field driven - rows are to be switched programmatically.

	CDPRETABLE_V4SPACING	  -  Use R4 spacing within the table so that the table is compatible with R4.

	CDPRETABLE_USEBORDERCOLOR	  -  Use a cell border color.

	CDPRETABLE_WIDTHSAMEASWINDOW	  -  Table width is set to fit to window.

	CDPRETABLE_SHOWTABS	  -  Set flags to create a tabbed table with the tabs on the top of the table. CDPRETABLE_FIELDDRIVEN must also be set. Also set the CDPRETABLEBEGIN ViewerType member to CDTABLEVIEWER_TABS.

	CDPRETABLE_SHOWTABSONLEFT	  -  Set flags to create a tabbed table with the tabs on the left side of the table. CDPRETABLE_FIELDDRIVEN must also be set. Also set the CDPRETABLEBEGIN ViewerType member to CDTABLEVIEWER_TABS.

	CDPRETABLE_SHOWTABSONBOTTOM	  -  Set flags to create a tabbed table with the tabs on the bottom of the table. CDPRETABLE_FIELDDRIVEN must also be set. Also set the CDPRETABLEBEGIN ViewerType member to CDTABLEVIEWER_TABS.

	CDPRETABLE_SHOWTABSONRIGHT	  -  Set flags to create a tabbed table with the tabs on the right side of the table. CDPRETABLE_FIELDDRIVEN must also be set. Also set the CDPRETABLEBEGIN ViewerType member to CDTABLEVIEWER_TABS.


**Description :**




**See Also :**
[CDPRETABLEBEGIN](/domino-c-api-docs/reference/Data/CDPRETABLEBEGIN)
---
