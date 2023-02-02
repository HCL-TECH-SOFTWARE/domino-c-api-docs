##### Data Type : Composite Data
##### CDLAYOUT - Start record for layout region on a form
---
##### #include <editods.h>
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
[CDLAYOUTBUTTON](D:/md_files/CDLAYOUTBUTTON.md)
[CDLAYOUTEND](D:/md_files/CDLAYOUTEND.md)
[CDLAYOUTFIELD](D:/md_files/CDLAYOUTFIELD.md)
[CDLAYOUTGRAPHIC](D:/md_files/CDLAYOUTGRAPHIC.md)
[CDLAYOUTTEXT](D:/md_files/CDLAYOUTTEXT.md)
[LAYOUT_FLAG_xxx](D:/md_files/LAYOUT_FLAG_xxx.md)
---
