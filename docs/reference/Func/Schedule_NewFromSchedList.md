##### Function : Calendaring and Scheduling
##### Schedule_NewFromSchedList - Adds a schedule to a schedule container
---
```
#include <schgtw.h>
STATUS LNPUBLIC Schedule_NewFromSchedList(

	HCNTNR  hCntnr,
	TIMEDATE_PAIR FAR *pInterval,
	SCHED_LIST FAR *pSchedList,
	char FAR *pUsername,
	STATUS  errStatus,
	DWORD  dwErrGateway,
	HSCHEDULE FAR *rethSched);
```
**Description :**

This routine addes a schedule to a schedule container.

**Parameters :**
Input :
hCntnr  -  A handle to the schedule container

pInterval  -  Points to the overall interval of the schedule.

pSchedList  -  Points to the SCHED_LIST

pUsername  -  The name of the owner of this schedule

errStatus  -  Domino error status returned if schedule couldn't be created.

dwErrGateway  -  Native gateway error returned if schedule couldn't be created.

Output :
(routine)  -  NOERROR - Successfully added a schedule.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethSched  -  Returns the HCNTNROBJ of the new schedule


**See Also :**
[Schedule_AddSchedList](/reference/Func/Schedule_AddSchedList)
[Schedule_ExtractMoreSchedList](/reference/Func/Schedule_ExtractMoreSchedList)
[Schedule_ExtractSchedList](/reference/Func/Schedule_ExtractSchedList)
[SCHED_LIST](/reference/Data/SCHED_LIST)
---
