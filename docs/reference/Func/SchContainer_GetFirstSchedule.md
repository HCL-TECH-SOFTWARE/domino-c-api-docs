##### Function : Calendaring and Scheduling
##### SchContainer_GetFirstSchedule - Get first schedule object in a container.
---
```
#include <schedule.h>
STATUS LNPUBLIC SchContainer_GetFirstSchedule(

	DHANDLE  hCntnr,
	HSCHEDULE FAR *rethObj,
	SCHEDULE FAR * FAR *retpSchedule);
```
**Description :**

This function is used to get a handle to the first schedule object in a 
container.

**Parameters :**
Input :
hCntnr  -  The container handle.

Output :
(routine)  -  NOERROR - Successfully got first schedule.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



rethObj  -  Points to where we return the handle to the schedule.

retpSchedule  -  Points to where we return a pointer to the actual data.


**See Also :**
[SchContainer_GetNextSchedule](/reference/Func/SchContainer_GetNextSchedule)
---
