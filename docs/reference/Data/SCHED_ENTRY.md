##### Data Type : Calendaring and Scheduling
##### SCHED_ENTRY - Scheduling busy time entry
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
   UNID          Unid;
   TIMEDATE_PAIR Interval;
   BYTE          Attr;
   BYTE          UserAttr;
   BYTE          spare[2];
} SCHED_ENTRY;
```

**Description :**

This is the data structure that describes an individual schedule entry.


**See Also :**
[SCHED_LIST](/domino-c-api-docs/reference/Data/SCHED_LIST)
---
