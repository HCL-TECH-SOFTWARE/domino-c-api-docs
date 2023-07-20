##### Data Type : Database
##### DBACTIVITYEXTENDED - Database Activity Extended Structure.
---
```
#include <nsfdb.h>
```

**Definition :**
```
typedef struct {
	TIMEDATE First;    /* Beginning of reporting period */
	TIMEDATE Last;    /* End of reporting period */
	DWORD Uses;     /* # of uses in reporting period */
	DWORD Reads;    /* # of reads in reporting period */
	DWORD Writes;    /* # of writes in reporting period */
	DWORD Adds;
	DWORD Updates;
	DWORD Deletes;
	DWORD PrevDayUses;   /* # of uses in previous 24 hours */
	DWORD PrevDayReads;   /* # of reads in previous 24 hours */
	DWORD PrevDayAdds;
	DWORD PrevDayUpdates;
	DWORD PrevDayDeletes;
	DWORD PrevWeekUses;   /* # of uses in previous week */
	DWORD PrevWeekReads;          /* # of reads in previous week */
	DWORD PrevWeekAdds;
	DWORD PrevWeekUpdates;
	DWORD PrevWeekDeletes;
	DWORD PrevMonthUses;         /* # of uses in previous month */
	DWORD PrevMonthReads;         /* # of reads in previous month */
	DWORD PrevMonthAdds;
	DWORD PrevMonthUpdates;
	DWORD PrevMonthDeletes;
} DBACTIVITYEXTENDED;
```

**Description :**

Database Activity Extended Structure.


**See Also :**
---
