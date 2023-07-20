##### Data Type : Calendaring and Scheduling
##### SCHED_ENTRY_EXT - Scheduling busy time entry extended
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
    UNID            Unid;       /* UNID of the entry */
    TIMEDATE_PAIR   Interval;   /* Interval of the entry */
    BYTE            Attr;       /* SCHED_ATTR_xxx attributes defined by Notes */
    BYTE            UserAttr;   /* Application specific attributes */
    BYTE            spare[2];
    
    /* Everything above this point is the same as SCHED_ENTRY for preR6 clients!
    ** Everything from here on down is R6 (or later) only!
    */

    UNID            ApptUnid;   /* ApptUNID of the entry */
    DWORD           dwEntrySize;/* Size of this entry (for future ease of 
expansion) */
    GEO_INFO        GEOInfo;    /* Geographical coordinates of the entry */
} SCHED_ENTRY_EXT;
```

**Description :**

This is the extended data structure that describes an individual schedule entry.


**See Also :**
[SCHED_ENTRY](/domino-c-api-docs/reference/Data/SCHED_ENTRY)
[SCHED_LIST](/domino-c-api-docs/reference/Data/SCHED_LIST)
---
