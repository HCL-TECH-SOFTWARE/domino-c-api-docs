##### Function : Calendaring and Scheduling
##### SchContainer_FindSchedule - Get a schedule.
---
##### #include <schedule.h>
STATUS LNPUBLIC **SchContainer_FindSchedule(**

	HCNTNR  hCntnr,
	char FAR *pszUserName,
	STATUS FAR *retErrStatus,
	DWORD FAR *retdwErrGateway,
	HSCHEDULE FAR *retvbObj,
	SCHEDULE FAR * FAR *retpSched);
**Description :**
This routine gets a schedule from the passed in container for a given user.
**Parameters :**
Input :
hCntnr  -  Points to the container.

pszUserName  -  The name of the user or NULL for the composite schedule.

Output :
(routine)  -  NOERROR - Successfully found a schedule.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



retErrStatus  -  Points to where we return the Domino error if there is one.

retdwErrGateway  -  Points to where we return the gateway error if there is one.

retvbObj  -  Points to  where we return the Vblock of sched object.

retpSched  -  Returns pointer to the schedule object.

**See Also :**
[SchContainer_GetFirstSchedule](D:/md_files/SchContainer_GetFirstSchedule.md)
[SchContainer_GetNextSchedule](D:/md_files/SchContainer_GetNextSchedule.md)
---
