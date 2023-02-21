##### Data Type : Navigators
##### VIEWMAP_RECT_RECORD - Navigator rectangle graphic CD record.
---
```
#include <vmods.h>
```
**Description :**

The VIEWMAP_RECT_RECORD stores a rectangle graphic (includes Rectangle, 
Ellipse, Round Rectangel, and Button objects) in a Navigator.  This record is 
stored in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the 
Navigator.  The fields in this structure are:

DRObj  Common fields, including VIEWMAP_RECT_RECORD signature.   See VMODSdrobj.
LineColor Color of the boundary line.   Use NOTES_COLOR_xxx value.
FillFGColor Foreground fill color.   Use NOTES_COLOR_xxx value.  
FillBGColor Background fill color.   Use NOTES_COLOR_xxx value.
LineStyle Style for the boundary line.   Use VM_LINE_xxx value.
LineWidth Width of the boundary line.
FillStyle  Style of rectangle fill.   Use VM_FILL_xxx value.
spare  Reserved;  must be 0.

This structure is followed by the name and the display label (if any, as 
defined by DRObj) in packed format (no terminating NUL).

**See Also :**
[VMODSdrobj](/domino-c-api-docs/reference/Data/VMODSdrobj)
---
