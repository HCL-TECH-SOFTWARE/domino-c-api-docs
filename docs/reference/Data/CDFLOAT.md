##### Data Type : Composite Data
##### CDFLOAT - Defines float position.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   BSIG Header; /* Signature and length of this record */
   WORD Float;  /* Vertical Alignment values */
} CDFLOAT;
```

**Description :**

Header	Signature and length of this record
<ul><br>
Float	Vertical alignment values, see (FLOAT_xxx).</ul>



**See Also :**
[FLOAT_xxx](/domino-c-api-docs/reference/Symb/FLOAT_xxx)
---
