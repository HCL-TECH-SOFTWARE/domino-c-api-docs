##### Data Type : Navigators
##### VIEWMAP_REGION_DEFAULTS - Default settings for Navigator regions.
---
```
#include <vmods.h>
```

**Definition :**
```
typedef struct {
   VIEWMAP_HIGHLIGHT_DEFAULTS Highlight;
} VIEWMAP_REGION_DEFAULTS;
```

**Description :**

The VIEWMAP_REGION_DEFAULTS structure contains default attributes for regions in the Navigator.  This structure is a component of the VIEWMAP_STYLE_DEFAULTS structure, which in turn is stored in the VIEWMAP_DATASET_RECORD.  The fields in this structure are:
<ul><br>

<ul>Highlight	Default highlight settings.</ul>
</ul>



**See Also :**
[VIEWMAP_HIGHLIGHT_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_HIGHLIGHT_DEFAULTS)
[VIEWMAP_STYLE_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_STYLE_DEFAULTS)
---
