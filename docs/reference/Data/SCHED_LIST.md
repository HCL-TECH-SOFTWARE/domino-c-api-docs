##### Data Type : Calendaring and Scheduling
##### SCHED_LIST - Calendar busy time schedule list structure
---
```
#include <nsfdata.h>
```

**Definition :**

typedef struct {
    DWORD   NumEntries;         /* Total number of schedule entries follow */
    WORD    wApplicationID;     /* Application id for UserAttr interpretation */
    WORD    Spare;              /* Pre Notes/Domino 6: spare 
                                ** Notes/Domino 6: This now conveys the length 
of a single
                                ** SCHED_ENTRY_xxx that follows.  Use this value
                                ** to skip entries that MAY be larger (ie: a 
later version may
                                ** extend SCHED_ENTRY_EXT by appending values
                                ** that Notes/Domino 6 does not know about so 
SCHED_ENTRY_xxx
                                ** would actually be larger than the 
Notes/Domino 6
                                ** SCHED_ENTRY_EXT
                                */
                                /* Now come the schedule entries... 
                                ** IF Spare==0 then SCHED_ENTRYs follow
                                ** Otherwise Spare==the length of the
                                ** SCHED_ENTRY_EXTs that follow
                                */
} SCHED_LIST;

**Description :**

This is the schedule data. The SCHED_LIST is followed by NumEntries of SCHED_ENTRY or SCHED_ENTRY_EXT.


**See Also :**
[Schedule_AddSchedList](/domino-c-api-docs/reference/Func/Schedule_AddSchedList)
[Schedule_NewFromSchedList](/domino-c-api-docs/reference/Func/Schedule_NewFromSchedList)
[SCHED_ENTRY](/domino-c-api-docs/reference/Data/SCHED_ENTRY)
[SCHED_ENTRY_EXT](/domino-c-api-docs/reference/Data/SCHED_ENTRY_EXT)
---
