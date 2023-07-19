##### Symbolic Value : Constants
##### VCF5_xxx - VIEW_COLUMN_FORMAT5 - dwFlags
---
```
#include <viewfmt.h>
```

**Symbolic Values :**

	VCF5_S_IS_NAME	  -  (Shift) Column contains a name.

	VCF5_M_IS_NAME	  -  (Mask) Column contains a name.

	VCF5_S_SHOW_IM_STATUS	  -  (Shift) Show IM online status in this column.

	VCF5_M_SHOW_IM_STATUS	  -  (Mask) Show IM online status in this column.	

	VCF5_S_VERT_ORIENT_TOP	  -  (Shift) Vertically show the icon on top line.

	VCF5_M_VERT_ORIENT_TOP	  -  (Mask) Vertically show the icon on top line.

	VCF5_S_VERT_ORIENT_MID	  -  (Shift) Vertically middle of the line entry.

	VCF5_M_VERT_ORIENT_MID	  -  (Mask) Vertically middle of the line entry.

	VCF5_S_VERT_ORIENT_BOTTOM	  -  (Shift) Show icon on the last line.

	VCF5_M_VERT_ORIENT_BOTTOM	  -  (Mask) Show icon on the last line.


**Description :**

The dwFlags field of the VIEW_COLUMN_FORMAT5 structure is a DWORD bit field of view attributes.  The Shift flags specify the first bit position for a specific attribute.  The Mask flags specify the bit mask (which bits are used) for a specific attribute.


**See Also :**
[VIEW_COLUMN_FORMAT5](/domino-c-api-docs/reference/Data/VIEW_COLUMN_FORMAT5)
---
