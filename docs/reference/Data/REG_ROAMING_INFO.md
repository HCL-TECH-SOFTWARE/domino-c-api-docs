##### Data Type : User Registration
##### REG_ROAMING_INFO - Structure that defines roaming registration information.
---
```
#include <reg.h>
```
**Description :**

This structure defines roaming registration information for the REGNewPerson 
function.  The entire structure must be initialized to zero.

The fields in the structure are (all fields that are not used must be NULL/O):

Size  Size of this structure - must be initialized with sizeof 
(REG_ROAMING_INFO).
ServerName Destination server name for the roaming files.
SubDirectory Path (relative) to data dir on which roaming files will be created.
CleanupSetting The cleanup setting used by the roaming client (see 
REG_ROAMING_CLEANUP_XXX).
CleanupPeriod Number of days between cleanup (1 - 365) for 
REG_ROAMING_CLEANUP_EVERY_NDAYS.
hReplicaServers (Optional.) Handle to a text list of server names where replica 
stubs of the roaming files should be created.  The list should be constructed 
with ListAllocate and ListAddEntry.  
    OnDuplicate      one of REG_FILE_DUP_XXX.
    Reserved  Reserved - must be 0.
pReserved  Reserved - must be NULL.


**See Also :**
[ListAddEntry](/reference/Func/ListAddEntry)
[ListAllocate](/reference/Func/ListAllocate)
[REGNewPerson](/reference/Func/REGNewPerson)
[REG_FILE_DUP_xxx](/reference/Symb/REG_FILE_DUP_xxx)
[REG_ROAMING_CLEANUP_xxx](/reference/Symb/REG_ROAMING_CLEANUP_xxx)
---
