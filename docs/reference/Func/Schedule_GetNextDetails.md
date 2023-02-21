##### Function : Calendaring and Scheduling
##### Schedule_GetNextDetails - Returns a handle to the next detail object for the schedule.
---
```
#include <schedule.h>
STATUS LNPUBLIC Schedule_GetNextDetails(

	HCNTNR  hCntnr,
	HCNTNROBJ  hDetailObj,
	HCNTNROBJ *rethNextDetailObj,
	SCHED_DETAIL_LIST FAR * FAR *retpNextDetail);
```
**Description :**

Returns a handle to the next detail object for the schedule.

**Parameters :**
Input :
hCntnr  -  Handle of container to get details from.

hDetailObj  -  The current detail object.

Output :
(routine)  -  Return status from this call: 

NOERROR 

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


rethNextDetailObj  -  Points to the next schedule.

retpNextDetail  -  Pointer to the pointer of the next detail.


**See Also :**
[HCNTNR](/domino-c-api-docs/reference/Data/HCNTNR)
[HCNTNROBJ](/domino-c-api-docs/reference/Data/HCNTNROBJ)
[SCHED_DETAIL_DATA](/domino-c-api-docs/reference/Data/SCHED_DETAIL_DATA)
[SCHED_DETAIL_ENTRY](/domino-c-api-docs/reference/Data/SCHED_DETAIL_ENTRY)
[SCHED_DETAIL_LIST](/domino-c-api-docs/reference/Data/SCHED_DETAIL_LIST)
---
