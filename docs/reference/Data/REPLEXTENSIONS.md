##### Data Type : Replication
##### REPLEXTENSIONS - Replication extension structure.
---
```
#include <repl.h>
```
**Description :**

To allow upwardly compatible changes with arbitrary additional parameters in 
ReplicateWithServer.  Only TimeLimit is defined for Release 4.  The parameter 
corresponding to this structure in ReplicateWithServerExt(), ExtendedOptions, 
may be set to NULL as a shorthand for passing a completely zeroed structure.

**See Also :**
[ReplicateWithServerExt](/domino-c-api-docs/reference/Func/ReplicateWithServerExt)
---
