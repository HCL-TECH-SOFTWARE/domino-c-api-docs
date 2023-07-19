##### Data Type : Calendaring and Scheduling
##### SCHEDULE - Data structure for a schedule.
---
```
#include <schedule.h>
```

**Definition :**

typedef struct {
   DWORD         reserved[8];
   DBID          dbReplicaID;      /* Users mail file replica ID */
   TIMEDATE_PAIR Interval;         /* events etc. are in this
                                      interval */
   DWORD         dwErrGateway;     /* gateway error retrieving this
                                      schedule */
   STATUS        error;            /* error retrieving this
                                      schedule */
   WORD          wReserved;        /* unused at this time */
   WORD          wOwnerNameSize;   /* size of owner name
                                      (includes term.) */
/* followed by owner name */
} SCHEDULE;

**Description :**

Data structure for a schedule.


**See Also :**
[SchContainer_GetFirstSchedule](/domino-c-api-docs/reference/Func/SchContainer_GetFirstSchedule)
[SchContainer_GetNextSchedule](/domino-c-api-docs/reference/Func/SchContainer_GetNextSchedule)
[SchContainer_FindSchedule](/domino-c-api-docs/reference/Func/SchContainer_FindSchedule)
---
