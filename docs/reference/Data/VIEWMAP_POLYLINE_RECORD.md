##### Data Type : Navigators
##### VIEWMAP_POLYLINE_RECORD - Navigator multiple-point line graphic CD record.
---
```
#include <vmods.h>
```

**Definition :**
```
typedef struct {
   VMODSbigobj DRobj;
   WORD        LineColor;
   WORD        LineStyle;
   WORD        LineWidth;
   WORD        nPts;
   DWORD       spare[4]; /* for future use */
} VIEWMAP_POLYLINE_RECORD;
```

**Description :**

Note:  The signature for this record has changed in Release 4.5 of Domino from a byte signature to a word signature.  The common fields structure has been changed from VMODSdrobj to VMODSbigobj.
<ul><br>
<br>
The VIEWMAP_POLYLINE_RECORD stores a line defined by multiple points in a Navigator.  This record is stored in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the Navigator.  The fields in this structure are:<br>
<br>
DRObj		Common fields, including VIEWMAP_POLYLINE_RECORD signature.   See VMODSbigobj.<br>
LineColor	Color of the line.   Use NOTES_COLOR_xxx value.<br>
LineStyle	Style for the line.   Use VM_LINE_xxx value.<br>
LineWidth	Width of the line.<br>
nPts		Number of points defining the line.<br>
spare		Reserved;  must be 0.<br>
<br>
This structure is followed by the name and the display label (if any) in packed format (no terminating NUL), then by an array of pairs of LONG values containing the coordinates for the line.  The number of pairs of values in this array is specified by the nPts field.</ul>



**See Also :**
[VMODSbigobj](/domino-c-api-docs/reference/Data/VMODSbigobj)
---
