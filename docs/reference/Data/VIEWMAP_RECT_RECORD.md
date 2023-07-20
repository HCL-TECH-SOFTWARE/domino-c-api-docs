##### Data Type : Navigators
##### VIEWMAP_RECT_RECORD - Navigator rectangle graphic CD record.
---
```
#include <vmods.h>
```

**Definition :**
```
typedef struct {
   VMODSdrobj DRobj;
   WORD       LineColor;
   WORD       FillFGColor;
   WORD       FillBGColor;
   WORD       LineStyle;
   WORD       LineWidth;
   WORD       FillStyle;
   DWORD      spare[4]; /* for future use */
} VIEWMAP_RECT_RECORD;
```

**Description :**

The VIEWMAP_RECT_RECORD stores a rectangle graphic (includes Rectangle, Ellipse, Round Rectangel, and Button objects) in a Navigator.  This record is stored in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the Navigator.  The fields in this structure are:
<ul><br>

<ul>DRObj		Common fields, including VIEWMAP_RECT_RECORD signature.   See VMODSdrobj.<br>
LineColor	Color of the boundary line.   Use NOTES_COLOR_xxx value.<br>
FillFGColor	Foreground fill color.   Use NOTES_COLOR_xxx value.  <br>
FillBGColor	Background fill color.   Use NOTES_COLOR_xxx value.<br>
LineStyle	Style for the boundary line.   Use VM_LINE_xxx value.<br>
LineWidth	Width of the boundary line.<br>
FillStyle		Style of rectangle fill.   Use VM_FILL_xxx value.<br>
spare		Reserved;  must be 0.</ul>
<br>
This structure is followed by the name and the display label (if any, as defined by DRObj) in packed format (no terminating NUL).</ul>



**See Also :**
[VMODSdrobj](/domino-c-api-docs/reference/Data/VMODSdrobj)
---
