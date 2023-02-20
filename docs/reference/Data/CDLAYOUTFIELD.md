##### Data Type : Composite Data
##### CDLAYOUTFIELD - Field definition within a layout region.
---
```
#include <editods.h>
```
**Description :**

A field in a layout region of a form is defined by a CDLAYOUTFIELD record.  
This record must be between a CDLAYOUT record and a CDLAYOUTEND record.  This 
record is usually followed by other CD records identifying text,  graphical, or 
action elements associated with the field.  The fields in this record are:

Header Defines this composite data item as a CDLAYOUTFIELD item.
ElementHeader Structure containing graphical attributes of the field (see 
ELEMENTHEADER).
Flags Flags for this field (see LAYOUT_FIELD_FLAG_xxx).
bFieldType Type of user interface for this element (see LAYOUT_FIELD_TYPE_xxx).


**See Also :**
[CDLAYOUT](/reference/Data/CDLAYOUT)
[CDLAYOUTBUTTON](/reference/Data/CDLAYOUTBUTTON)
[CDLAYOUTEND](/reference/Data/CDLAYOUTEND)
[CDLAYOUTGRAPHIC](/reference/Data/CDLAYOUTGRAPHIC)
[CDLAYOUTTEXT](/reference/Data/CDLAYOUTTEXT)
[ELEMENTHEADER](/reference/Data/ELEMENTHEADER)
[LAYOUT_FIELD_FLAG_xxx](/reference/Symb/LAYOUT_FIELD_FLAG_xxx)
[LAYOUT_FIELD_TYPE_xxx](/reference/Symb/LAYOUT_FIELD_TYPE_xxx)
---
