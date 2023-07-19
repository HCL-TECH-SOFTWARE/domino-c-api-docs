##### Data Type : Composite Data
##### CDLAYOUTGRAPHIC - Graphical element definition within a layout region.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   BSIG           Header;
   ELEMENTHEADER  ElementHeader;
   DWORD          Flags;
   BYTE           Reserved[16];
} CDLAYOUTGRAPHIC;

**Description :**

A graphical element in a layout region of a form is defined by a CDLAYOUTGRAPHIC record.  This record must be between a CDLAYOUT record and a CDLAYOUTEND record.  This record is usually followed by other CD records identifying text,  graphical, or action elements associated with the graphical element.  The fields in this record are:<br>

<ul>
<ul>Header	Defines this composite data item as a CDLAYOUTGRAPHIC item.<br>
ElementHeader	Structure containing graphical attributes of the element (see ELEMENTHEADER).<br>
Flags	Flags for this element (see LAYOUT_GRAPHIC_FLAG_xxx).</ul>
</ul>



**See Also :**
[CDLAYOUT](/domino-c-api-docs/reference/Data/CDLAYOUT)
[CDLAYOUTBUTTON](/domino-c-api-docs/reference/Data/CDLAYOUTBUTTON)
[CDLAYOUTEND](/domino-c-api-docs/reference/Data/CDLAYOUTEND)
[CDLAYOUTFIELD](/domino-c-api-docs/reference/Data/CDLAYOUTFIELD)
[CDLAYOUTTEXT](/domino-c-api-docs/reference/Data/CDLAYOUTTEXT)
[ELEMENTHEADER](/domino-c-api-docs/reference/Data/ELEMENTHEADER)
[LAYOUT_GRAPHIC_FLAG_xxx](/domino-c-api-docs/reference/Symb/LAYOUT_GRAPHIC_FLAG_xxx)
---
