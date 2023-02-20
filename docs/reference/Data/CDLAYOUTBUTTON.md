##### Data Type : Composite Data
##### CDLAYOUTBUTTON - Button definition within a layout region.
---
```
#include <editods.h>
```
**Description :**

A button in a layout region of a form is defined by a CDLAYOUTBUTTON record.  
This record must be between a CDLAYOUT record and a CDLAYOUTEND record.  This 
record is usually followed by other CD records identifying text,  graphical, or 
action elements associated with the button.  The fields in this record are:

Header Defines this composite data item as a CDLAYOUTBUTTON item.
ElementHeader Structure containing graphical attributes of the button (see 
ELEMENTHEADER).
Flags Flags for this button (no flags are currently defined).


**See Also :**
[CDLAYOUT](/reference/Data/CDLAYOUT)
[CDLAYOUTEND](/reference/Data/CDLAYOUTEND)
[CDLAYOUTFIELD](/reference/Data/CDLAYOUTFIELD)
[CDLAYOUTGRAPHIC](/reference/Data/CDLAYOUTGRAPHIC)
[CDLAYOUTTEXT](/reference/Data/CDLAYOUTTEXT)
[ELEMENTHEADER](/reference/Data/ELEMENTHEADER)
---
