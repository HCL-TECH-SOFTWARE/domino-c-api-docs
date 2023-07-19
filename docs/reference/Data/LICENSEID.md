##### Data Type : IDs
##### LICENSEID - Structure defining a license number.
---
```
#include <global.h>
```

**Definition :**

typedef struct {
   BYTE ID[5];    /* license number */
   BYTE Product;  /* product code, mfgr-specific */
   BYTE Check[2]; /* validity check field, mfgr-specific */
} LICENSEID;

**Description :**

This is the structure that defines a license number.  Since this may change in future releases, do not attempt to interpret this structure.  For now, simply treat the entire structure as a unique ID.


**See Also :**
[SECKFMUserInfo](/domino-c-api-docs/reference/Func/SECKFMUserInfo)
---
