##### Data Type : Composite Data
##### CDLAYOUTTEXT - Text element definition within a layout region.
---
##### #include <editods.h>
**Description :**
A text element in a layout region of a form is defined by a CDLAYOUTTEXT 
record.  This record must be between a CDLAYOUT record and a CDLAYOUTEND 
record.  This record is usually followed by other CD records identifying text,  
graphical, or action elements associated with the element.  The fields in this 
record are:

Header Defines this composite data item as a CDLAYOUTTEXT item.
ElementHeader Structure containing graphical attributes of the field (see 
ELEMENTHEADER).
Flags Flags for this field (see LAYOUT_TEXT_FLAG_xxx).

This record may be followed by 8-bit text data, if the record was created by an 
early Test Build of Notes Release 4.0.  Normally, other CD records will follow 
containing the text and graphical elements associated with this text element.

**See Also :**
[CDLAYOUT](D:/md_files/CDLAYOUT.md)
[CDLAYOUTBUTTON](D:/md_files/CDLAYOUTBUTTON.md)
[CDLAYOUTEND](D:/md_files/CDLAYOUTEND.md)
[CDLAYOUTFIELD](D:/md_files/CDLAYOUTFIELD.md)
[CDLAYOUTGRAPHIC](D:/md_files/CDLAYOUTGRAPHIC.md)
[ELEMENTHEADER](D:/md_files/ELEMENTHEADER.md)
[LAYOUT_TEXT_FLAG_xxx](D:/md_files/LAYOUT_TEXT_FLAG_xxx.md)
---
