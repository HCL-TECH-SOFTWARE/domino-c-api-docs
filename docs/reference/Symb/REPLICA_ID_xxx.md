##### Symbolic Value : Replica Info
##### REPLICA_ID_xxx - Known Replica IDs.
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	REPLICA_ID_UNINITIALIZED	  -  Uninitialized ID.

	REPLICA_ID_CATALOG	  -  Database Catalog (Version 2).

	REPLICA_ID_EVENT	  -  Stats & Events Config DB.

	REPLICA_ID_NEVERREPLICATE	  -  Do not allow replicas. This known replica ID is now OBSOLETE. Although the replicator still supports it, the problem is that DBs that use it cannot have DocLinks to them. Instead use the replica flag REPLFLG_NEVER_REPLICATE.


**Description :**

Used in ID.Time field in ReplicaID (ID member of the DBREPLICAINFO structure). Date subfield must be REPLICA_DATE_RESERVED).<br>
<br>
 The format is as follows:  Least significant byte is version number.  2nd byte represents package code but is hard-coded to protect against changes in the package code. Most sig. 2 bytes are reserved for future use.


**See Also :**
[DBREPLICAINFO](/domino-c-api-docs/reference/Data/DBREPLICAINFO)
[REPLICA_DATE_RESERVED](/domino-c-api-docs/reference/Symb/REPLICA_DATE_RESERVED)
---
