##### Symbolic Value : Views
##### VIEW_TABLE_xxx (VIEW_TABLE_FORMAT) - VIEW_TABLE_FORMAT - Flags2
---
```
#include <viewfmt.h>
```

**Symbolic Values :**

	VIEW_TABLE_FLAT_HEADINGS	  -  TRUE if we should display no-borders at all on the header.

	VIEW_TABLE_COLORIZE_ICONS	  -  TRUE if the icons displayed in the view should be colorized.

	VIEW_TABLE_HIDE_SB	  -  TRUE if we should not display a search bar for this view.

	VIEW_TABLE_HIDE_CAL_HEADER	  -  TRUE if we should hide the calendar header.

	VIEW_TABLE_NOT_CUSTOMIZED	  -  TRUE if view has not been customized (i.e. not saved by Designer).


**Description :**

These flags help define the format  used when a view is displayed. The Flags2 word of the VIEW_TABLE_FORMAT structure contains a value constructed by combining these flags using bitwise-OR.


**See Also :**
[VIEW_TABLE_FORMAT](/domino-c-api-docs/reference/Data/VIEW_TABLE_FORMAT)
---
