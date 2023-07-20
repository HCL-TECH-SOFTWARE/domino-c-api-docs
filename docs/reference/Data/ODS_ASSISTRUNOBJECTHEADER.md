##### Data Type : Agents
##### ODS_ASSISTRUNOBJECTHEADER - Header for objects added by an Agent.
---
```
#include <queryods.h>
```

**Definition :**
```
typedef struct {
   DWORD dwFlags;  /* flags */
   WORD  wEntries; /* Number of entries following */
   WORD  wSpare;
/* entries follow */
} ODS_ASSISTRUNOBJECTHEADER;
```

**Description :**

When an Agent is run, results may be generated and stored as objects following the Agent.  The header contains the number of ODS_ASSISTRUNOBJECTENTRY records that follow.


**See Also :**
[ODS_ASSISTRUNOBJECTENTRY](/domino-c-api-docs/reference/Data/ODS_ASSISTRUNOBJECTENTRY)
[ODS_ASSISTSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTSTRUCT)
---
