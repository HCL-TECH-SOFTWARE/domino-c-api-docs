##### Function : Calendaring and Scheduling
##### Schedule_AddSchedList - Add a SCHED_LIST entry
---
```
#include <schgtw.h>
STATUS LNPUBLIC Schedule_AddSchedList(

	HCNTNR  hCntnr,
	HCNTNROBJ  hSched,
	TIMEDATE_PAIR FAR *pInterval,
	SCHED_LIST FAR *pSchedList,
	HCNTNROBJ FAR *rethSchedList);
```
**Description :**

This adds more schedlist entries to an existing schedule. Note: This call 
expects that the caller add the sched lists in order of earlier timedates to 
later timedates.

**Parameters :**
Input :
hCntnr  -  A handle to the schedule container.

hSched  -  A handle to an existing schedule.

pInterval  -  Points to the overall interval of the schedule. Note: Entries not in this interval are removed.

pSchedList  -  Points to the SCHED_LIST

Output :
(routine)  -  NOERROR - Successfully added a SCHED_LIST entry.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethSchedList  -  Returns the HCNTNROBJ of the new sched list.


**See Also :**
[SCHED_LIST](/reference/Data/SCHED_LIST)
---
