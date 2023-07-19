##### Data Type : Composite Data
##### FRAMESETLENGTH - Used to specify the ROWS or COLS attributes for a frameset element
---
```
#include <fsods.h>
```

**Definition :**

typedef struct {
   WORD Type;  /* see xxx_LengthType */
   WORD Value; /* The value of the ROWS or COLS attribute */
} FRAMESETLENGTH;

**Description :**

One structure for each row or column.


**See Also :**
[CDFRAMESET](/domino-c-api-docs/reference/Data/CDFRAMESET)
---
