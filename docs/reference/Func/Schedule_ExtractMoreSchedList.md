##### Function : Calendaring and Scheduling
##### Schedule_ExtractMoreSchedList - Extract more schedule list information.
---
```
#include <schedule.h>
STATUS LNPUBLIC Schedule_ExtractMoreSchedList(

	HCNTNR  hCntnr,
	HCNTNROBJ  hMoreCtx,
	TIMEDATE_PAIR FAR *pInterval,
	DWORD FAR *retdwSize,
	DHANDLE FAR *rethSchedList,
	HCNTNROBJ FAR *rethMore);
```
**Description :**

This retrieves more schedule list information.

**Parameters :**
Input :
hCntnr  -  The handle to the container of the schedule.

hMoreCtx  -  The handle to more schedule list information that was returned by previous calls to Schedule_ExtractMoreSchedList and Schedule_ExtractSchedList. 

Output :
(routine)  -  NOERROR - Successfully extracted more schedule list information.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


pInterval  -  Point to where the interval of the schedule is returned.

retdwSize  -  Points to where the size of the range is returned.

rethSchedList  -  Points to where a handle to the schedule list associated with this schedule object is returned. Callers must free this when they're done.

rethMore  -  If not NULLCNTNROBJ then this is the handle to more schedule list information.


**See Also :**
[Schedule_ExtractMoreSchedList](/domino-c-api-docs/reference/Func/Schedule_ExtractMoreSchedList)
---
