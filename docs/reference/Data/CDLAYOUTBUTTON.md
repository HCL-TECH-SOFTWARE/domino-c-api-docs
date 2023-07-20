##### Data Type : Composite Data
##### CDLAYOUTBUTTON - Button definition within a layout region.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   BSIG           Header;
 ELEMENTHEADER  ElementHeader;
 DWORD          Flags;
 BYTE           Reserved[16];
} CDLAYOUTBUTTON;
```

**Description :**

A button in a layout region of a form is defined by a CDLAYOUTBUTTON record.  This record must be between a CDLAYOUT record and a CDLAYOUTEND record.  This record is usually followed by other CD records identifying text,  graphical, or action elements associated with the button.  The fields in this record are:<br>

<ul>
<ul>Header	Defines this composite data item as a CDLAYOUTBUTTON item.<br>
ElementHeader	Structure containing graphical attributes of the button (see ELEMENTHEADER).<br>
Flags	Flags for this button (no flags are currently defined).</ul>
</ul>



**See Also :**
[CDLAYOUT](/domino-c-api-docs/reference/Data/CDLAYOUT)
[CDLAYOUTEND](/domino-c-api-docs/reference/Data/CDLAYOUTEND)
[CDLAYOUTFIELD](/domino-c-api-docs/reference/Data/CDLAYOUTFIELD)
[CDLAYOUTGRAPHIC](/domino-c-api-docs/reference/Data/CDLAYOUTGRAPHIC)
[CDLAYOUTTEXT](/domino-c-api-docs/reference/Data/CDLAYOUTTEXT)
[ELEMENTHEADER](/domino-c-api-docs/reference/Data/ELEMENTHEADER)
---
