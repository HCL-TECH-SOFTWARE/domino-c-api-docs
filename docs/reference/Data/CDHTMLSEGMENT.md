##### Data Type : Composite Data
##### CDHTMLSEGMENT - Reserved for future use.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;
   WORD wHTMLLength; /* Length of raw HTML */
/* HTML, the variable part of the struct... */
} CDHTMLSEGMENT;
```

**Description :**

This record is included for future use.  Applications should not generate these records.  Domino and Notes will ignore this record.


**See Also :**
[CDHTMLHEADER](/domino-c-api-docs/reference/Data/CDHTMLHEADER)
---
