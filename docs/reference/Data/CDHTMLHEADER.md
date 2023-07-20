##### Data Type : Composite Data
##### CDHTMLHEADER - Reserved for future use
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;
   WORD wSegments; /* Number of HTML segments */
} CDHTMLHEADER;
```

**Description :**

This record is included for future use.  Applications should not generate these records.  Domino and Notes will ignore this record.


**See Also :**
[CDHTMLSEGMENT](/domino-c-api-docs/reference/Data/CDHTMLSEGMENT)
---
