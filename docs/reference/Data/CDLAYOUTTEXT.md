##### Data Type : Composite Data
##### CDLAYOUTTEXT - Text element definition within a layout region.
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
/* For records saved with builds prior to 134,
   the 8-bit text string follows... */
} CDLAYOUTTEXT;

**Description :**

A text element in a layout region of a form is defined by a CDLAYOUTTEXT record.  This record must be between a CDLAYOUT record and a CDLAYOUTEND record.  This record is usually followed by other CD records identifying text,  graphical, or action elements associated with the element.  The fields in this record are:<br>

<ul>
<ul>Header	Defines this composite data item as a CDLAYOUTTEXT item.<br>
ElementHeader	Structure containing graphical attributes of the field (see ELEMENTHEADER).<br>
Flags	Flags for this field (see LAYOUT_TEXT_FLAG_xxx).</ul>
</ul>

<ul>This record may be followed by 8-bit text data, if the record was created by an early Test Build of Notes Release 4.0.  Normally, other CD records will follow containing the text and graphical elements associated with this text element.</ul>



**See Also :**
[CDLAYOUT](/domino-c-api-docs/reference/Data/CDLAYOUT)
[CDLAYOUTBUTTON](/domino-c-api-docs/reference/Data/CDLAYOUTBUTTON)
[CDLAYOUTEND](/domino-c-api-docs/reference/Data/CDLAYOUTEND)
[CDLAYOUTFIELD](/domino-c-api-docs/reference/Data/CDLAYOUTFIELD)
[CDLAYOUTGRAPHIC](/domino-c-api-docs/reference/Data/CDLAYOUTGRAPHIC)
[ELEMENTHEADER](/domino-c-api-docs/reference/Data/ELEMENTHEADER)
[LAYOUT_TEXT_FLAG_xxx](/domino-c-api-docs/reference/Symb/LAYOUT_TEXT_FLAG_xxx)
---
