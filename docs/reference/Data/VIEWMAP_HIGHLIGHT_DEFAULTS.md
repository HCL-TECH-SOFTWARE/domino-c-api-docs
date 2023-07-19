##### Data Type : Navigators
##### VIEWMAP_HIGHLIGHT_DEFAULTS - Default highlight settings for Navigator elements.
---
```
#include <vmods.h>
```

**Definition :**

typedef struct {
   WORD   bHighlightTouch;
   WORD   bHighlightCurrent;
   WORD   HLOutlineColor;
   WORD   HLOutlineWidth;
   WORD   HLOutlineStyle;
   WORD   HLFillColor; 
} VIEWMAP_HIGHLIGHT_DEFAULTS;

**Description :**

The VIEWMAP_HIGHLIGHT_DEFAULTS structure stores default settings for highlighting the graphical elements of a Navigator.  This structure is common to all the VIEWMAP_xxx_DEFAULTS structures.  The fields in this structure are:
<ul><br>

<ul>bHighlightTouch	If TRUE, highlight elements when touched.<br>
bHighlightCurrent	If TRUE, highlight when element is the current element.<br>
HLOutlineColor		Color to use for the outline of a highlighted element.<br>
HLOutlineWidth	Width of the outline of a highlighted element.<br>
HLOutlineStyle		Style for the outline of a highlighted element.<br>
HLFillColor		Fill color to use for a highlighted element.</ul>
</ul>



**See Also :**
[VIEWMAP_SHAPE_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_SHAPE_DEFAULTS)
[VIEWMAP_LINE_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_LINE_DEFAULTS)
[VIEWMAP_REGION_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_REGION_DEFAULTS)
[VIEWMAP_BUTTON_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_BUTTON_DEFAULTS)
[VIEWMAP_BITMAP_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_BITMAP_DEFAULTS)
[VIEWMAP_TEXTBOX_DEFAULTS](/domino-c-api-docs/reference/Data/VIEWMAP_TEXTBOX_DEFAULTS)
---
