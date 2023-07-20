##### Data Type : Navigators
##### VIEWMAP_STYLE_DEFAULTS - Default settings for Navigator elements.
---
```
#include <vmods.h>
```

**Definition :**
```
typedef struct {
   VIEWMAP_SHAPE_DEFAULTS   Shapes;
   VIEWMAP_LINE_DEFAULTS    Lines;
   VIEWMAP_REGION_DEFAULTS  Regions;
   VIEWMAP_BUTTON_DEFAULTS  Buttons;
   VIEWMAP_BITMAP_DEFAULTS  Bitmaps;
   VIEWMAP_TEXTBOX_DEFAULTS TextBoxes;
} VIEWMAP_STYLE_DEFAULTS;
```

**Description :**

The VIEWMAP_STYLE_DEFAULTS structure stores the default settings for the display of graphical elements in a Navigator.  This structure contains the other VIEWMAP_xxx_DEFAULTS records.  This structure is, in turn, a component of a VIEWMAP_DATASET_RECORD CD record.


**See Also :**
[VIEWMAP_SHAPE_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_SHAPE_DEFAULTS)
[VIEWMAP_LINE_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_LINE_DEFAULTS)
[VIEWMAP_REGION_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_REGION_DEFAULTS)
[VIEWMAP_BUTTON_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_BUTTON_DEFAULTS)
[VIEWMAP_BITMAP_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_BITMAP_DEFAULTS)
[VIEWMAP_TEXTBOX_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_TEXTBOX_DEFAULTS)
[VIEWMAP_DATASET_RECORD](/domino-c-api-docs/reference/Data/VIEWMAP_DATASET_RECORD)
---
