##### Function : Calendaring and Scheduling
##### Schedule_Free - Frees a schedule from within a container.
---
```
#include <schgtw.h>
STATUS LNPUBLIC Schedule_Free(

	HCNTNR  hCntnr,
	HSCHEDULE  hSched);
```
**Description :**

This routine frees a schedule from within a container.

**Parameters :**
Input :
hCntnr  -  Handle of schedule container.

hSched  -  The HCNTNROBJ of the schedule to free.

Output :
(routine)  -  NOERROR - Successfully freed schedule.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**See Also :**
[SchContainer_FindSchedule](/domino-c-api-docs/reference/Func/SchContainer_FindSchedule)
[SchContainer_GetFirstSchedule](/domino-c-api-docs/reference/Func/SchContainer_GetFirstSchedule)
[SchContainer_GetNextSchedule](/domino-c-api-docs/reference/Func/SchContainer_GetNextSchedule)
[Schedule_NewFromSchedList](/domino-c-api-docs/reference/Func/Schedule_NewFromSchedList)
---
