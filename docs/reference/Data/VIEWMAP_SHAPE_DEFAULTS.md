##### Data Type : Navigators
##### VIEWMAP_SHAPE_DEFAULTS - Default settings for Navigator shapes.
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
   FONTID FontID;
} VIEWMAP_SHAPE_DEFAULTS;
```

**Description :**

The VIEWMAP_SHAPE_DEFAULTS structure contains default attributes for shapes in the Navigator.  This structure is a component of the VIEWMAP_STYLE_DEFAULTS structure, which in turn is stored in the VIEWMAP_DATASET_RECORD.  The fields in this structure are:
<ul><br>

<ul>Highlight	Default highlight settings.<br>
LineColor	Default line color.<br>
FillFGColor	Default fill color for foreground.<br>
FillBGColor	Default fill color for background.<br>
LineStyle	Default line style.<br>
LineWidth	Default line width.<br>
FillStyle	Default fill style.<br>
FontID		Default Font ID for label text.</ul>
</ul>



**See Also :**
[VIEWMAP_HIGHLIGHT_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_HIGHLIGHT_DEFAULTS)
[VIEWMAP_STYLE_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_STYLE_DEFAULTS)
---
