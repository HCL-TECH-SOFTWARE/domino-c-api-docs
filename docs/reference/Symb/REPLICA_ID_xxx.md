##### Symbolic Value : Replica Info
##### REPLICA_ID_xxx - Known Replica IDs.
---
```
#include <nsfdata.h>
```
**Description :**

Used in ID.Time field in ReplicaID (ID member of the DBREPLICAINFO structure). 
Date subfield must be REPLICA_DATE_RESERVED).

 The format is as follows:  Least significant byte is version number.  2nd byte 
represents package code but is hard-coded to protect against changes in the 
package code. Most sig. 2 bytes are reserved for future use.

**See Also :**
[DBREPLICAINFO](/reference/Data/DBREPLICAINFO)
[REPLICA_DATE_RESERVED](/reference/Symb/REPLICA_DATE_RESERVED)
---
