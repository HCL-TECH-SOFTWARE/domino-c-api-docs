##### Symbolic Value : Navigators
##### VM_DSET_xxx - Option flags for VIEWMAP_DATASET_RECORD.
---
```
#include <vmods.h>
```

**Symbolic Values :**

	VM_DSET_SHOW_GRID	  -  Show the grid in design mode.

	VM_DSET_SNAPTO_GRID	  -  Snap to grid.

	VM_DSET_SAVE_IMAGEMAP	  -  Save a bitmap image of the navigator for use by Web browsers.

	VM_DSET_READING_ORDER_RTL	  -  reading order


**Description :**

These option flags are stored in the Flags field of the VIEWMAP_DATASET_RECORD.
<ul><br>
<br>
If the flag VM_DSET_SAVE_IMAGEMAP is set, a bitmap image of the navigator is generated and stored.  When this navigator is accessed through a Domino server, the bitmap image is displayed in the browser.</ul>



**See Also :**
[VIEWMAP_DATASET_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_DATASET_RECORD)
---
