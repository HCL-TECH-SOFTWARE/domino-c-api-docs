##### Function : Calendaring and Scheduling
##### Schedule_ExtractMoreBusyTimeRange - Extracts more busy time information.
---
##### #include <schedule.h>
STATUS LNPUBLIC **Schedule_ExtractMoreBusyTimeRange(**

	HCNTNR  hCntnr,
	HCNTNROBJ  hMoreCtx,
	const UNID *punidIgnore,
	TIMEDATE_PAIR *pInterval,
	DWORD *retdwSize,
	DHANDLE *rethRange,
	HCNTNROBJ *rethMore);
**Description :**
This is the continuation of the process begun with 
Schedule_ExtractBusyTimeRange.
**Parameters :**
Input :
hCntnr  -  The handle to the container of the schedule.

hMoreCtx  -  The handle to more information that we got back from Schedule_ExtractBusyTimeRange.

punidIgnore  -  Points to UNID to ignore in busy time calculation.

Output :
(routine)  -  NOERROR - Successfully extracted busy time range.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


pInterval  -  Points to where we return the overall interval of the schedule.

retdwSize  -  The size of the range returned.

rethRange  -  Points to where we return a handle to the time range associated with this schedule.

rethMore  -  If not NULLCNTNROBJ then this is the handle to more busytime information. This handle is passed to Schedule_ExtractMoreBusyTimeRange.

**See Also :**
[Schedule_ExtractBusyTimeRange](D:/md_files/Schedule_ExtractBusyTimeRange.md)
---
