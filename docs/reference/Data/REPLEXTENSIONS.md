##### Data Type : Replication
##### REPLEXTENSIONS - Replication extension structure.
---
```
#include <repl.h>
```

**Definition :**
```
typedef struct {
   WORD     Size;      /* sizeof(REPLEXTENSIONS), allows for future
                          expansion */
   WORD     TimeLimit; /* If non-zero, number of minutes replication
                          is allowed to execute before cancellation.
                          If not specified, no limit is imposed */
} REPLEXTENSIONS;
```

**Description :**

To allow upwardly compatible changes with arbitrary additional parameters in ReplicateWithServer.  Only TimeLimit is defined for Release 4.  The parameter corresponding to this structure in ReplicateWithServerExt(), ExtendedOptions, may be set to NULL as a shorthand for passing a completely zeroed structure.


**See Also :**
[ReplicateWithServerExt](/domino-c-api-docs/reference/Func/ReplicateWithServerExt)
---
