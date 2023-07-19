##### Data Type : Composite Data
##### CDCOLOR - Specifies the Paper Color.
---
```
#include <colorods.h>
```

**Definition :**

typedef struct {
   BSIG Header;  /* Signature and length of this record */
   COLOR_VALUE Color;
} CDCOLOR;

**Description :**

This CD Record identifies the paper color for a given document.
<ul><br>
<br>
Header		Identifies this as a CDCOLOR record.<br>
COLOR_VALUE	CD Structure defining the components of paper color.</ul>



**See Also :**
[COLOR_VALUE](/domino-c-api-docs/reference/Data/COLOR_VALUE)
[COLOR_VALUE_FLAGS_xxx](/domino-c-api-docs/reference/Symb/COLOR_VALUE_FLAGS_xxx)
---
