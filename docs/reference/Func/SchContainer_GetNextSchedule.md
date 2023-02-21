##### Function : Calendaring and Scheduling
##### SchContainer_GetNextSchedule - Get a handle to the next schedule object.
---
```
#include <schedule.h>
STATUS LNPUBLIC SchContainer_GetNextSchedule(

	DHANDLE  hCntnr,
	HSCHEDULE  hCurSchedule,
	HSCHEDULE FAR *rethNextSchedule,
	SCHEDULE FAR * FAR *retpNextSchedule);
```
**Description :**

This routine is used to get a handle to the next schedule object in a 
container.

**Parameters :**
Input :
hCntnr  -  The container handle.

hCurSchedule  -  The current schedule.

Output :
(routine)  -  NOERROR - Successfully got the next schedule.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethNextSchedule  -  A handle to the next schedule

retpNextSchedule  -  Points to where we return the pointer to the actual data.


**See Also :**
[SchContainer_GetFirstSchedule](/domino-c-api-docs/reference/Func/SchContainer_GetFirstSchedule)
---
