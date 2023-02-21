##### Function : Database
##### REPL_GET_PRIORITY - Return replication priority value.
---
```
#include <nsfdata.h>
WORD REPL_GET_PRIORITY(

	WORD  Flags);
```
**Description :**

Extracts the replication priority value from the replication flags word of the 
DBREPLICAINFO structure.  This function is implemented as a macro:

#define REPL_GET_PRIORITY(Flags) \
 (((Flags >> REPLFLG_PRIORITY_SHIFT)+1) & REPLFLG_PRIORITY_MASK)

**Parameters :**
Input :
Flags  -  Flag word containing the replication priority flags.

Output :
(routine)  -  Replication priority value.  The priority value may be:

    0  Low
    1  Medium
    2  High




**See Also :**
[NSFDbReplicaInfoGet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoGet)
[NSFDbReplicaInfoSet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoSet)
[DBREPLICAINFO](/domino-c-api-docs/reference/Data/DBREPLICAINFO)
[REPL_SET_PRIORITY](/domino-c-api-docs/reference/Func/REPL_SET_PRIORITY)
---
