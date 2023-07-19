##### Data Type : Agents
##### ODS_ASSISTRUNOBJECTENTRY - Record containing the length of an object added by an Agent.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   DWORD dwLength;
   DWORD dwFlags;
} ODS_ASSISTRUNOBJECTENTRY;

**Description :**

When an Agent is run, results may be generated and stored as objects following the Agent.  Each object is preceded with a record containing the length of the object.


**See Also :**
[ODS_ASSISTRUNOBJECTHEADER](/domino-c-api-docs/reference/Data/ODS_ASSISTRUNOBJECTHEADER)
[ODS_ASSISTSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTSTRUCT)
---
