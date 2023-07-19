##### Data Type : Agents
##### ODS_ASSISTRUNINFO - Agent run record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   TIMEDATE LastRun;     /* Time of last agent run */
   DWORD    dwProcessed; /* Number of docs processed on last run */
   TIMEDATE AssistMod;   /* Time of last assistant modification */
   TIMEDATE DbID;        /* DbID on which assistant was last run */
   LONG     dwExitCode;  /* Exit code when assistant was last run */
   DWORD    dwSpare[4];
} ODS_ASSISTRUNINFO;

**Description :**

Each time an Agent is run, a record is written containing information about that execution.


**See Also :**
[ODS_ASSISTRUNOBJECTENTRY](/domino-c-api-docs/reference/Data/ODS_ASSISTRUNOBJECTENTRY)
[ODS_ASSISTRUNOBJECTHEADER](/domino-c-api-docs/reference/Data/ODS_ASSISTRUNOBJECTHEADER)
[ODS_ASSISTSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTSTRUCT)
---
