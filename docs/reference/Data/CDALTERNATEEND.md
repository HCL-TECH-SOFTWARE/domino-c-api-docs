##### Data Type : Composite Data
##### CDALTERNATEEND - End of alternate display records.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   BSIG  Header; /* Signature and length of this record */
   DWORD Flags;  /* Unused; must be 0 */
} CDALTERNATEEND;
```

**Description :**

This record marks the end of a sequence of CD records comprising the alternate representation of an active object.  For more information, please see the entry for CDALTERNATEBEGIN.  The fields in this record are:
<ul><br>

<ul>Header	Identifies this as a CDALTERNATEEND record<br>
Flags	Currently unused;  must be 0</ul>
</ul>



**See Also :**
[CDALTERNATEBEGIN](/domino-c-api-docs/reference/Data/CDALTERNATEBEGIN)
---
