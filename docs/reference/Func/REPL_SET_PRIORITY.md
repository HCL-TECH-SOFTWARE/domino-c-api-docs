##### Function : Database
##### REPL_SET_PRIORITY - Set the replication priority value.
---
```
#include <nsfdata.h>
WORD REPL_SET_PRIORITY(

	WORD  Pri);
```
**Description :**

Stores the new replication priority value into the replication flags word 
stored in the DBREPLICAINFO structure.  This function is implemented as a macro:

#define REPL_SET_PRIORITY(Pri) \
 (((Pri - 1) & REPLFLG_PRIORITY_MASK) << REPLFLG_PRIORITY_SHIFT)

**Parameters :**
Input :
Pri  -  New priority value to set:

    0  Low
    1  Medium
    2  High

Output :
(routine)  -  Flag word with new priority value set.



**See Also :**
[NSFDbReplicaInfoGet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoGet)
[NSFDbReplicaInfoSet](/domino-c-api-docs/reference/Func/NSFDbReplicaInfoSet)
[DBREPLICAINFO](/domino-c-api-docs/reference/Data/DBREPLICAINFO)
[REPL_GET_PRIORITY](/domino-c-api-docs/reference/Func/REPL_GET_PRIORITY)
---
