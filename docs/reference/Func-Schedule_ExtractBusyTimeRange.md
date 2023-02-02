##### Function : Calendaring and Scheduling
##### Schedule_ExtractBusyTimeRange - Retrieve a RANGE from a schedule.
---
##### #include <schedule.h>
STATUS LNPUBLIC **Schedule_ExtractBusyTimeRange(**

	HCNTNR  hCntnr,
	HCNTNROBJ  hSchedObj,
	const UNID FAR *punidIgnore,
	TIMEDATE_PAIR FAR *pInterval,
	DWORD FAR *retdwSize,
	DHANDLE FAR *rethRange,
	HCNTNROBJ *rethMoreCtx);
**Description :**
This routine retrieves a RANGE from a schedule that specifies all a users' busy 
times. It returns a handle to the memory where the range has been placed.  
Note: submitting a range or time that is in the past is not supported.
**Parameters :**
Input :
hCntnr  -  The handle to the container of the schedule.

hSchedObj  -  the HCNTROBJ of the schedule object

punidIgnore  -  Points to the UNID to ignore in busy time calculations

Output :
(routine)  -  NOERROR - Successfully extracted busy time range.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


pInterval  -  Points to where we return the overall interval of the schedule

retdwSize  -  The size of the range returned.

rethRange  -  Points to where we return a handle to the time range associated with this schedule. Note: Callers must free this when they're done.

rethMoreCtx  -  If not NULLCNTNROBJ, then this is the handle to more busy time information. This handle is passed to Schedule_ExtractMoreBusyTimeRange()

**Sample Usage :**
```
	/* Extract the busy times */
 if (error = Schedule_ExtractBusyTimeRange(rethCntnr, hSchedObj, &theApptUnid, 
&pInterval, &retdwSize, &rethRange, &hMoreObj))
	 LAPI_RETURN (ERR(error));
```
**See Also :**
[Schedule_ExtractFreeTimeRange](D:/md_files/Schedule_ExtractFreeTimeRange.md)
[Schedule_ExtractMoreBusyTimeRange](D:/md_files/Schedule_ExtractMoreBusyTimeRange.md)
---
