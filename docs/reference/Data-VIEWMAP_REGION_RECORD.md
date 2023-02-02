##### Data Type : Navigators
##### VIEWMAP_REGION_RECORD - Navigator region graphic CD record.
---
##### #include <vmods.h>
**Description :**
The VIEWMAP_REGION_RECORD stores a region graphic in a Navigator.  This record 
is stored in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the 
Navigator.  The fields in this structure are:

DRObj  Common fields, including VIEWMAP_REGION_RECORD signature.   See 
VMODSdrobj.
LineColor Color of the boundary line.   Use NOTES_COLOR_xxx value.
LineStyle Style for the boundary line.   Use VM_LINE_xxx value.
LineWidth Width of the boundary line.
FillStyle  Style of region fill.   Use VM_FILL_xxx value.
spare  Reserved;  must be 0.

This structure is followed by the name and the display label (if any) in packed 
format (no terminating NUL).

If the record represents a circle (SIG_CD_VMCIRCLE), the center of the circle 
will be the center of the rectangle for this region, and the radius will be 
one-half the width of the rectangle.
**See Also :**
[VMODSdrobj](D:/md_files/VMODSdrobj.md)
---
