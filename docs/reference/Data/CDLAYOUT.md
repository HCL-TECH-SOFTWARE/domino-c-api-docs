##### Data Type : Composite Data
##### CDLAYOUT - Start record for layout region on a form
---
```
#include <editods.h>
```

**Definition :**

typedef struct{
   BSIG   Header;
   WORD   wLeft;
   WORD   wWidth;
   WORD   wHeight;
   DWORD  Flags;
   WORD   wGridSize;
   BYTE   Reserved[14];
} CDLAYOUT;

**Description :**

The definition for a layout region on a form is stored as CD records in the $Body item of the form note.  The layout region begins with a CDLAYOUT record and ends with a CDLAYOUTEND record.  Other records in the layout region define buttons, graphics, fields, or other rich text elements.  The fields in this record are:<br>

<ul>
<ul>Header	Defines this composite data item as a CDLAYOUT item.<br>
wLeft	Left margin of the layout region in &quot;twips&quot;<br>
wWidth	Width of the layout region in &quot;twips&quot;<br>
wHeight	Height of the layout region in &quot;twips&quot;<br>
Flags	Flags for this layout region (see LAYOUT_FLAG_xxx)<br>
wGridSize	Spacing of grid points in &quot;twips&quot;</ul>
</ul>



**See Also :**
[CDLAYOUTBUTTON](/domino-c-api-docs/reference/Data/CDLAYOUTBUTTON)
[CDLAYOUTEND](/domino-c-api-docs/reference/Data/CDLAYOUTEND)
[CDLAYOUTFIELD](/domino-c-api-docs/reference/Data/CDLAYOUTFIELD)
[CDLAYOUTGRAPHIC](/domino-c-api-docs/reference/Data/CDLAYOUTGRAPHIC)
[CDLAYOUTTEXT](/domino-c-api-docs/reference/Data/CDLAYOUTTEXT)
[LAYOUT_FLAG_xxx](/domino-c-api-docs/reference/Symb/LAYOUT_FLAG_xxx)
---
