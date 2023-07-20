##### Data Type : Navigators
##### VIEWMAP_POLYGON_RECORD - Navigator polygon graphic CD record.
---
```
#include <vmods.h>
```

**Definition :**
```
typedef struct {
   VMODSbigobj DRobj;
   WORD        LineColor;
   WORD        FillFGColor;
   WORD        FillBGColor;
   WORD        LineStyle;
   WORD        LineWidth;
   WORD        FillStyle;
   WORD        nPts;
   DWORD       spare[4]; /* for future use */
} VIEWMAP_POLYGON_RECORD;
```

**Description :**

Note:  The signature for this record has changed in Release 4.5 of Domino from a byte signature to a word signature.  The common fields structure has been changed from VMODSdrobj to VMODSbigobj.
<ul><br>
<br>
The VIEWMAP_POLYGON_RECORD stores a bitmap in a Navigator.  This record is stored in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the Navigator.  The fields in this structure are:<br>
<br>
DRObj		Common fields, including VIEWMAP_POLYGON_RECORD signature.   See VMODSbigobj.<br>
LineColor	Color of the boundary line.   Use NOTES_COLOR_xxx value.<br>
FillFGColor	Foreground fill color.   Use NOTES_COLOR_xxx value.<br>
FillBGColor	Background fill color.   Use NOTES_COLOR_xxx value.<br>
LineStyle	Style for the boundary line.   Use VM_LINE_xxx value.<br>
LineWidth	Width of the boundary line.<br>
FillStyle		Style for polygon fill.   Use VM_FILL_xxx value.<br>
nPts		Number of points defining this polygon.<br>
spare		Reserved;  must be 0.<br>
<br>
This structure is followed by the name and the display label (if any) in packed format (no terminating NUL), then by an array of pairs of LONG values containing the coordinates for the polygon.  The number of pairs of values in this array is specified by the nPts field.</ul>



**See Also :**
[VMODSbigobj](/domino-c-api-docs/reference/Data/VMODSbigobj)
---
