##### Data Type : Replication
##### REPLFILESTATS - Replication statistics structure.
---
```
#include <repl.h>
```

**Definition :**

typedef struct {
   long TotalFiles;
   long FilesCompleted;
   long NotesAdded;
   long NotesDeleted;
   long NotesUpdated;
   long Successful;
   long Failed;
   long NumberErrors;
} REPLFILESTATS;

**Description :**

This structure is returned by ReplicateWithServer() and ReplicateWithServerExt().  It contains the resulting replication statistics information.


**See Also :**
[ReplicateWithServer](/domino-c-api-docs/reference/Func/ReplicateWithServer)
[ReplicateWithServerExt](/domino-c-api-docs/reference/Func/ReplicateWithServerExt)
---
