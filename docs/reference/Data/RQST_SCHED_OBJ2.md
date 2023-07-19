##### Data Type : Calendaring and Scheduling
##### RQST_SCHED_OBJ2 - Scheduling Reply/Request object.
---
```
#include <schgtw.h>
```

**Definition :**

typedef struct {
    DWORD           dwOptions;       /* SCHRQST_xxx option codes (see 
schedule.h)*/
    WORD            wNumHops;        /* Number of hops so far */
    TIMEDATE_PAIR   Interval;        /* Interval */
    UNID            ApptUnid;        /* UNID of appt to ignore busytime for */
    TIMEDATE        ApptOrigDate;    /* (Orginizer 2.x) the orig date of 
ignored appt */
    DWORD           reserved[10];
    WORD            wClientNamesSize; /* Queryer's name length */
    WORD            wServerNameSize; /* Notes server name length (includes 
term.) */
    /* The rest is new as of Build 173 */
    DWORD           dwRequestHdrLen;    /* Size of this request header */
    DWORD           dwDetailListSize;   /* Size of detailed item list  */
    DWORD           dwiCalListSize;     /* Size of iCalendar list */
    DWORD           dwWebUserNameLen;   /* Length of Web User Name to Follow */
    DWORD           dwWebPasswordLen;   /* Length of Web Password to Follow  */
    DWORD           Spare[10];          /* Keep a bunch of extra space - BAK */
/* Followed by:
**  List of Client names (or proxy) doing the query (may be NULL),
**  Name of Notes server to forward this request to (NULL terminated).
**  List of item names to get detailed information from (may be NULL),
**  List of names/URLs pairs to get iCalendar schedules from (may be NULL)
**  Web User Name to send to authenticating proxy, if any (may be NULL),
**  Web Password to send to authentiating prox, if any (may be NULL)
**
** Note that the dwRequestHdrLen is used so that if we need to expand
** the SCHED_REQ size in the future for some reason, the older (as of R6)
** receiver can parse what they know and skip the newer stuff that MUST
** ALWAYS be appended to the structure (but that comes before the expected 
** data listed above!!)
*/
} RQST_SCHED_OBJ2;

**Description :**

Scheduling Reply/Request object used in Domino/Notes 6 and later.


**See Also :**
---
