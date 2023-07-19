##### Data Type : Composite Data
##### CDLAYOUTEND - Record marking the end of a layout region.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   BSIG  Header;
   BYTE  Reserved[16];
} CDLAYOUTEND;

**Description :**

The CDLAYOUTEND record marks the end of the elements defining a layout region within a form.  The fields in this record are:<br>

<ul>
<ul>Header	Defines this composite data item as a CDLAYOUTEND item.</ul>
</ul>



**See Also :**
[CDLAYOUT](/domino-c-api-docs/reference/Data/CDLAYOUT)
[CDLAYOUTBUTTON](/domino-c-api-docs/reference/Data/CDLAYOUTBUTTON)
[CDLAYOUTFIELD](/domino-c-api-docs/reference/Data/CDLAYOUTFIELD)
[CDLAYOUTGRAPHIC](/domino-c-api-docs/reference/Data/CDLAYOUTGRAPHIC)
[CDLAYOUTTEXT](/domino-c-api-docs/reference/Data/CDLAYOUTTEXT)
---
