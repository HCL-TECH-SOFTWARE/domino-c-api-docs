##### Data Type : Navigators
##### VIEWMAP_LINE_DEFAULTS - Default settings for lines in Navigators.
---
```
#include <vmods.h>
```

**Definition :**
```
typedef struct {
   VIEWMAP_HIGHLIGHT_DEFAULTS Highlight;
   WORD   LineColor;
   WORD   FillFGColor;
   WORD   FillBGColor;
   WORD   LineStyle;
   WORD   LineWidth;
   WORD   FillStyle;
} VIEWMAP_LINE_DEFAULTS;
```

**Description :**

The VIEWMAP_LINE_DEFAULTS structure contains default attributes for lines in the Navigator.  This structure is a component of the VIEWMAP_STYLE_DEFAULTS structure, which in turn is stored in the VIEWMAP_DATASET_RECORD.  The fields in this structure are:
<ul><br>

<ul>Highlight	Default highlight settings.<br>
LineColor	Default color for lines.<br>
FillFGColor	Default foreground color.<br>
FillBGColor	Default background color.<br>
LineStyle	Default line style.<br>
LineWidth	Default line width.<br>
FillStyle	Default fill style.</ul>
</ul>



**See Also :**
[VIEWMAP_HIGHLIGHT_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_HIGHLIGHT_DEFAULTS)
[VIEWMAP_STYLE_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_STYLE_DEFAULTS)
---
