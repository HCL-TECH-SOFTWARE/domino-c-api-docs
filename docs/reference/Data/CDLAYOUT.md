##### Data Type : Composite Data
##### CDLAYOUT - Start record for layout region on a form
---
```
#include <editods.h>
```
**Description :**

The definition for a layout region on a form is stored as CD records in the 
$Body item of the form note.  The layout region begins with a CDLAYOUT record 
and ends with a CDLAYOUTEND record.  Other records in the layout region define 
buttons, graphics, fields, or other rich text elements.  The fields in this 
record are:

Header Defines this composite data item as a CDLAYOUT item.
wLeft Left margin of the layout region in "twips"
wWidth Width of the layout region in "twips"
wHeight Height of the layout region in "twips"
Flags Flags for this layout region (see LAYOUT_FLAG_xxx)
wGridSize Spacing of grid points in "twips"


**See Also :**
[CDLAYOUTBUTTON](/reference/Data/CDLAYOUTBUTTON)
[CDLAYOUTEND](/reference/Data/CDLAYOUTEND)
[CDLAYOUTFIELD](/reference/Data/CDLAYOUTFIELD)
[CDLAYOUTGRAPHIC](/reference/Data/CDLAYOUTGRAPHIC)
[CDLAYOUTTEXT](/reference/Data/CDLAYOUTTEXT)
[LAYOUT_FLAG_xxx](/reference/Symb/LAYOUT_FLAG_xxx)
---
