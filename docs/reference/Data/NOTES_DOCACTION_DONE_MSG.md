##### Data Type : Notes/FX data
##### NOTES_DOCACTION_DONE_MSG - Message passed to OLE FX server upon the completion of an executed Doc Action.
---
```
#include <olenotes.h>
```

**Definition :**
```
typedef struct {
   int   ActionID;  /* Doc action ID which has completed execution */
   DWORD ExecuteStatus; /* Execution status
                           0 = SUCCESS, Non-zero internal failure. */
   DWORD Unused[3]; /* Future use */
} NOTES_DOCACTION_DONE_MSG;
```

**Description :**

Message passed to OLE FX server upon the completion of an executed Doc Action.


**See Also :**
---
