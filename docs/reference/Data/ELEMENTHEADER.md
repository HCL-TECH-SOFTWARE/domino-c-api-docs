##### Data Type : Rich Text
##### ELEMENTHEADER - Common fields in CDLAYOUTxxx records.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WORD        wLeft;
   WORD        wTop;
   WORD        wWidth;
   WORD        wHeight;
   FONTID      FontID;          /* Font ID */
   BYTE        byBackColor;     /* Background color */
   BYTE        bSpare;
   COLOR_VALUE BackgroundColor; /* v5.0 background color */
} ELEMENTHEADER;

**Description :**

This structure contains the common fields for the graphical elements in a layout region of a form.  The fields in this structure are:
<ul><br>
<br>
wLeft		Location of the left edge of the element in twips<br>
wTop		Location of the top of the element in twips<br>
wWidth		Width of the element in twips<br>
wHeight		Height of the element in twips<br>
FontID		Font used to display text in the element<br>
byBackColor	Background color for the element<br>
bSpare<br>
BackgroundColor	Release 5.0 Backgroun color</ul>



**See Also :**
[CDLAYOUTBUTTON](/domino-c-api-docs/reference/Data/CDLAYOUTBUTTON)
[CDLAYOUTFIELD](/domino-c-api-docs/reference/Data/CDLAYOUTFIELD)
[CDLAYOUTGRAPHIC](/domino-c-api-docs/reference/Data/CDLAYOUTGRAPHIC)
[CDLAYOUTTEXT](/domino-c-api-docs/reference/Data/CDLAYOUTTEXT)
---
