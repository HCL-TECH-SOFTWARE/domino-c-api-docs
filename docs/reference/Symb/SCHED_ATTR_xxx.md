##### Symbolic Value : Calendaring and Scheduling
##### SCHED_ATTR_xxx - SCHED_ENTRY - Attr
---
```
#include <nsfdata.h>
```
**Description :**

Possible values for the Attr member of the SCHED_ENTRY structure.  Note that if 
bit 3 (bits are numbered from 0 to 7) is set, the entry will take up busy 
time.  The lower nibble of the attributes defines the the entry type.

NOTE:  The upper two bits of the Attr field is reserved for future use (bit 6 - 
7).

**See Also :**
[SCHED_ENTRY](/domino-c-api-docs/reference/Data/SCHED_ENTRY)
---
