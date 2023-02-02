##### Function : Calendaring and Scheduling
##### Schedule_ExtractSchedList - Extract a schedule list.
---
##### #include <schedule.h>
STATUS LNPUBLIC **Schedule_ExtractSchedList(**

	HCNTNR  hCntnr,
	HCNTNROBJ  hSchedObj,
	TIMEDATE_PAIR FAR *pInterval,
	DWORD FAR *retdwSize,
	DHANDLE FAR *rethSchedList,
	HCNTNROBJ FAR *rethMore);
**Description :**
This retrieves a schedule list from a schedule and returns a handle to the 
memory where the schedule list has been placed.
**Parameters :**
Input :
hCntnr  -  The handle to the container of the schedule.

hSchedObj  -  The HCNTNROBJ of the schedule object.

Output :
(routine)  -  NOERROR - Successfully extracted a schedule list.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


pInterval  -  Points to where the overall interval of the schedul is returned.

retdwSize  -  Where the size of the range is returned.

rethSchedList  -  Points to where we return a handle to the schedule list associated with this schedule. Callers must free this when they're done.

rethMore  -  If not NULLCNTNROBJ then this is the handle to more busytime information. This handle is passed to Schedule_ExtractMoreSchedList.

**See Also :**
[Schedule_ExtractMoreSchedList](D:/md_files/Schedule_ExtractMoreSchedList.md)
---
