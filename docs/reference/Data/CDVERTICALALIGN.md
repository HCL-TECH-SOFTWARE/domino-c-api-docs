##### Data Type : Composite Data
##### CDVERTICALALIGN - Specifies vertical alignment structure.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   BSIG Header;    /* Signature and length of this record */
   WORD Alignment; /* Vertical Alignment values */
} CDVERTICALALIGN;

**Description :**

This CD record allows for additional information to be provided for a graphic.
<ul><br>
<br>
BSIG	Header		Signature and length of this record.<br>
WORD	Alignment	see VERTICAL_ALIGNMENT_xxx</ul>



**See Also :**
[CDGRAPHIC](/domino-c-api-docs/reference/Data/CDGRAPHIC)
[VERTICAL_ALIGNMENT_xxx](/domino-c-api-docs/reference/Symb/VERTICAL_ALIGNMENT_xxx)
---
