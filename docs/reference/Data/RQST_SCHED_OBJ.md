##### Data Type : Calendaring and Scheduling
##### RQST_SCHED_OBJ - Scheduling Reply/Request object.
---
```
#include <schgtw.h>
```

**Definition :**
```
typedef struct {
   DWORD         dwOptions;        /* see SCHRQST_xxx */
   WORD          wNumHops;         /* number of hops so far */
   TIMEDATE_PAIR Interval;         /* interval */
   UNID          ApptUnid;         /* Unid of appt to ignore
                                      busytime for */
   TIMEDATE      ApptOrigDate;     /* (Orginizer 2.x) the orig date
                                      of ignored appt */
   DWORD         reserved[10];
   WORD          wClientNamesSize; /* queryer's name length
                                      (includes term.) */
   WORD          wServerNameSize;  /* Lotus Domino Server name length
                                      (includes term.) */
/* Followed by Client name doing the query (NULL terminated) */
/* Followed by name of Lotus Domino Server to forward this request to
  (NULL terminated). */
} RQST_SCHED_OBJ;
```

**Description :**

Scheduling Reply/Request object.


**See Also :**
[SCHRQST_xxx](/domino-c-api-docs/reference/Symb/SCHRQST_xxx)
[SchContainer_GetRequest](/domino-c-api-docs/reference/Func/SchContainer_GetRequest)
---
