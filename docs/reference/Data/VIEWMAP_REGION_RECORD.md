##### Data Type : Navigators
##### VIEWMAP_REGION_RECORD - Navigator region graphic CD record.
---
```
#include <vmods.h>
```

**Definition :**

typedef struct {
   VMODSdrobj DRobj;
   WORD       LineColor;
   WORD       LineStyle;
   WORD       LineWidth;
   WORD       FillStyle;
   DWORD      spare[4];  /* for future use */
} VIEWMAP_REGION_RECORD;

**Description :**

The VIEWMAP_REGION_RECORD stores a region graphic in a Navigator.  This record is stored in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the Navigator.  The fields in this structure are:
<ul><br>

<ul>DRObj		Common fields, including VIEWMAP_REGION_RECORD signature.   See VMODSdrobj.<br>
LineColor	Color of the boundary line.   Use NOTES_COLOR_xxx value.<br>
LineStyle	Style for the boundary line.   Use VM_LINE_xxx value.<br>
LineWidth	Width of the boundary line.<br>
FillStyle		Style of region fill.   Use VM_FILL_xxx value.<br>
spare		Reserved;  must be 0.</ul>
<br>
This structure is followed by the name and the display label (if any) in packed format (no terminating NUL).<br>
<br>
If the record represents a circle (SIG_CD_VMCIRCLE), the center of the circle will be the center of the rectangle for this region, and the radius will be one-half the width of the rectangle.</ul>



**See Also :**
[VMODSdrobj](/domino-c-api-docs/reference/Data/VMODSdrobj)
---
