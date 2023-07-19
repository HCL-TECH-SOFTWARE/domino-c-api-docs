##### Data Type : Views
##### IXCOLUMNTEXTDESC - Formatted column text descriptor.
---
```
#include <ixview.h>
```

**Definition :**

typedef struct {
   WORD Width;             /* Column width in 1/8 characters */
   WORD Position;          /* Column position in characters */
   FLAG Alignment:2;       /* Alignment (left, right, etc. ) */
   FLAG LastColumn:1;      /* Last column flag */
   FLAG Category:1;        /* Column is a category flag */
   WORD TextMax;           /* Text space allocated for this column */
   WORD TextLength;        /* Text string length */
/* char Text[TextMax]; */ /* Text string itself */
} IXCOLUMNTEXTDESC;

**Description :**

This is a data structure used to store text information extracted from the NIF Summary information for exports of view data into text.


**See Also :**
[IXCOLDESC](/domino-c-api-docs/reference/Data/IXCOLDESC)
---
