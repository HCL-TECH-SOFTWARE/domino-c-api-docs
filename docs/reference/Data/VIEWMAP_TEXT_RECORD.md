##### Data Type : Navigators
##### VIEWMAP_TEXT_RECORD - Navigator text graphic CD record.
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
   DWORD       spare[4]; /* for future use */
} VIEWMAP_TEXT_RECORD;
```

**Description :**

The VIEWMAP_TEXT_RECORD stores text to be displayed in a Navigator.  This record is stored in items of type TYPE_VIEWMAP_LAYOUT, the graphical layout of the Navigator.  The fields in this structure are:
<ul><br>

<ul>DRObj		Common fields, including VIEWMAP_TEXT_RECORD signature.   See VMODSbigobj.<br>
LineColor	Color of the boundary line.   Use NOTES_COLOR_xxx value.<br>
FillFGColor	Foreground fill color.   Use NOTES_COLOR_xxx value.<br>
FillBGColor	Background fill color.   Use NOTES_COLOR_xxx value.<br>
LineStyle	Style for the boundary line.   Use VM_LINE_xxx value.<br>
LineWidth	Width of the boundary line.<br>
FillStyle		Style for textbox fill.   Use VM_FILL_xxx value.<br>
spare		Reserved;  must be 0.</ul>
<br>
This structure is followed by the name and the display label (if any) in packed format (no terminating NUL).</ul>



**See Also :**
[VMODSbigobj](/domino-c-api-docs/reference/Data/VMODSbigobj)
---
