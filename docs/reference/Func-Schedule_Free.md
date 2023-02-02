##### Function : Calendaring and Scheduling
##### Schedule_Free - Frees a schedule from within a container.
---
##### #include <schgtw.h>
STATUS LNPUBLIC **Schedule_Free(**

	HCNTNR  hCntnr,
	HSCHEDULE  hSched);
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
[SchContainer_FindSchedule](D:/md_files/SchContainer_FindSchedule.md)
[SchContainer_GetFirstSchedule](D:/md_files/SchContainer_GetFirstSchedule.md)
[SchContainer_GetNextSchedule](D:/md_files/SchContainer_GetNextSchedule.md)
[Schedule_NewFromSchedList](D:/md_files/Schedule_NewFromSchedList.md)
---
