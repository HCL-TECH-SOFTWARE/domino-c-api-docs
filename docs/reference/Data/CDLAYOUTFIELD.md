##### Data Type : Composite Data
##### CDLAYOUTFIELD - Field definition within a layout region.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   BSIG           Header;
   ELEMENTHEADER  ElementHeader;
   DWORD          Flags;
   BYTE           bFieldType;
   BYTE           Reserved[15];
} CDLAYOUTFIELD;

**Description :**

A field in a layout region of a form is defined by a CDLAYOUTFIELD record.  This record must be between a CDLAYOUT record and a CDLAYOUTEND record.  This record is usually followed by other CD records identifying text,  graphical, or action elements associated with the field.  The fields in this record are:<br>

<ul>
<ul>Header	Defines this composite data item as a CDLAYOUTFIELD item.<br>
ElementHeader	Structure containing graphical attributes of the field (see ELEMENTHEADER).<br>
Flags	Flags for this field (see LAYOUT_FIELD_FLAG_xxx).<br>
bFieldType	Type of user interface for this element (see LAYOUT_FIELD_TYPE_xxx).</ul>
</ul>



**See Also :**
[CDLAYOUT](/domino-c-api-docs/reference/Data/CDLAYOUT)
[CDLAYOUTBUTTON](/domino-c-api-docs/reference/Data/CDLAYOUTBUTTON)
[CDLAYOUTEND](/domino-c-api-docs/reference/Data/CDLAYOUTEND)
[CDLAYOUTGRAPHIC](/domino-c-api-docs/reference/Data/CDLAYOUTGRAPHIC)
[CDLAYOUTTEXT](/domino-c-api-docs/reference/Data/CDLAYOUTTEXT)
[ELEMENTHEADER](/domino-c-api-docs/reference/Data/ELEMENTHEADER)
[LAYOUT_FIELD_FLAG_xxx](/domino-c-api-docs/reference/Symb/LAYOUT_FIELD_FLAG_xxx)
[LAYOUT_FIELD_TYPE_xxx](/domino-c-api-docs/reference/Symb/LAYOUT_FIELD_TYPE_xxx)
---
