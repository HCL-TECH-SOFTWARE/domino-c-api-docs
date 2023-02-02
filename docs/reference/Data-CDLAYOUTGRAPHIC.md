##### Data Type : Composite Data
##### CDLAYOUTGRAPHIC - Graphical element definition within a layout region.
---
##### #include <editods.h>
**Description :**
A graphical element in a layout region of a form is defined by a 
CDLAYOUTGRAPHIC record.  This record must be between a CDLAYOUT record and a 
CDLAYOUTEND record.  This record is usually followed by other CD records 
identifying text,  graphical, or action elements associated with the graphical 
element.  The fields in this record are:

Header Defines this composite data item as a CDLAYOUTGRAPHIC item.
ElementHeader Structure containing graphical attributes of the element (see 
ELEMENTHEADER).
Flags Flags for this element (see LAYOUT_GRAPHIC_FLAG_xxx).

**See Also :**
[CDLAYOUT](D:/md_files/CDLAYOUT.md)
[CDLAYOUTBUTTON](D:/md_files/CDLAYOUTBUTTON.md)
[CDLAYOUTEND](D:/md_files/CDLAYOUTEND.md)
[CDLAYOUTFIELD](D:/md_files/CDLAYOUTFIELD.md)
[CDLAYOUTTEXT](D:/md_files/CDLAYOUTTEXT.md)
[ELEMENTHEADER](D:/md_files/ELEMENTHEADER.md)
[LAYOUT_GRAPHIC_FLAG_xxx](D:/md_files/LAYOUT_GRAPHIC_FLAG_xxx.md)
---
