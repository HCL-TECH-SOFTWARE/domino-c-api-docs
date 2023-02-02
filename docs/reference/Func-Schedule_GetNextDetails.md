##### Function : Calendaring and Scheduling
##### Schedule_GetNextDetails - Returns a handle to the next detail object for the schedule.
---
##### #include <schedule.h>
STATUS LNPUBLIC **Schedule_GetNextDetails(**

	HCNTNR  hCntnr,
	HCNTNROBJ  hDetailObj,
	HCNTNROBJ *rethNextDetailObj,
	SCHED_DETAIL_LIST FAR * FAR *retpNextDetail);
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
[HCNTNR](D:/md_files/HCNTNR.md)
[HCNTNROBJ](D:/md_files/HCNTNROBJ.md)
[SCHED_DETAIL_DATA](D:/md_files/SCHED_DETAIL_DATA.md)
[SCHED_DETAIL_ENTRY](D:/md_files/SCHED_DETAIL_ENTRY.md)
[SCHED_DETAIL_LIST](D:/md_files/SCHED_DETAIL_LIST.md)
---
