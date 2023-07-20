##### Data Type : Database
##### DBACTIVITY - Database Activity Structure
---
```
#include <nsfdb.h>
```

**Definition :**
```
typedef struct {
   TIMEDATE First;           /* Beginning of reporting period */
   TIMEDATE Last;            /* End of reporting period */
   DWORD    Uses;            /* # of uses in reporting period */
   DWORD    Reads;           /* # of reads in reporting period */
   DWORD    Writes;          /* # of writes in reporting period */
   DWORD    PrevDayUses;     /* # of uses in previous 24 hours */
   DWORD    PrevDayReads;    /* # of reads in previous 24 hours */
   DWORD    PrevDayWrites;   /* # of writes in previous 24 hours */
   DWORD    PrevWeekUses;    /* # of uses in previous week */
   DWORD    PrevWeekReads;   /* # of reads in previous week */
   DWORD    PrevWeekWrites;  /* # of writes in previous week */
   DWORD    PrevMonthUses;   /* # of uses in previous month */
   DWORD    PrevMonthReads;  /* # of reads in previous month */
   DWORD    PrevMonthWrites; /* # of writes in previous month */
} DBACTIVITY;
```

**Description :**

This structure is returned by NSFDbGetUserActivity().  It contains the total of the database usage statistics for the prior day, week, and month, and since user activity recording began.


**See Also :**
[DBACTIVITY_ENTRY](/domino-c-api-docs/reference/Data/DBACTIVITY_ENTRY)
[NSFDbGetActivityUserNamePtr](/domino-c-api-docs/reference/Func/NSFDbGetActivityUserNamePtr)
[NSFDbGetUserActivity](/domino-c-api-docs/reference/Func/NSFDbGetUserActivity)
---
