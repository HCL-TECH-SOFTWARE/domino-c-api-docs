##### Data Type : Replication
##### REPLSERVSTATS - Replication statistics.
---
```
#include <repl.h>
```

**Definition :**
```
typedef struct {
   REPLFILESTATS Pull;
   REPLFILESTATS Push;
   long StubsInitialized;
   long TotalUnreadExchanges;
   long NumberErrors;
   STATUS LastError;
} REPLSERVSTATS;
```

**Description :**

This structure is returned from ReplicateWithServer and ReplicateWithServerExt.  It contains the returned replication statistics.


**See Also :**
[ReplicateWithServer](/domino-c-api-docs/reference/Func/ReplicateWithServer)
[ReplicateWithServerExt](/domino-c-api-docs/reference/Func/ReplicateWithServerExt)
---
