##### Symbolic Value : Database
##### REPLFLG_xxx - Replication Flags.
---
```
#include <nsfdata.h>
```
**Description :**

These flags are used by the Server's Replicator Task to control just what is 
done and not done during the replication process on a per-database level.

Note that you cannot set the replicate database title, categories, and template 
option with the C API.

The flags REPALFLG_DO_NOT_CATALOG, REPALFLG_HIDDEN_DESIGN, 
REPLFLG_DO_NOT_BROWSE, and REPALFLG_NO_CHRONOS refer to the Database 
Information, Other Settings options.

Note the distinction between REPLFLG_DISABLE and REPLFLG_NEVER_REPLICATE. The 
former is used to temporarily disable replication.  The latter is used to 
indicate that this database should NEVER be replicated.  The former may be set 
and cleared by the Notes user interface. The latter is intended to be set 
programmatically and SHOULD NEVER be able to be cleared by the user interface.  
The latter was invented to avoid having to set the replica ID to the known 
value of REPLICA_ID_NEVERREPLICATE.  This latter method has the failing that 
databases  that use it cannot have DocLinks to them.

**See Also :**
[NSFDbReplicaInfoGet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoGet)
[NSFDbReplicaInfoSet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoSet)
[DBREPLICAINFO](/domino-c-api-docs/reference/Data/DBREPLICAINFO)
---
