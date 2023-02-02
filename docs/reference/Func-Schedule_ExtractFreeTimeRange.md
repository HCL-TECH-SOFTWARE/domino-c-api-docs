##### Function : Calendaring and Scheduling
##### Schedule_ExtractFreeTimeRange - Retrieve a RANGE from a schedule
---
##### #include <schedule.h>
STATUS LNPUBLIC **Schedule_ExtractFreeTimeRange(**

	HCNTNR  hCntnr,
	HCNTNROBJ  hSchedObj,
	const UNID FAR *punidIgnore,
	BOOL  fFindFirstFit,
	WORD  wDuration,
	TIMEDATE_PAIR FAR *pInterval,
	DWORD FAR *retdwSize,
	DHANDLE FAR *rethRange);
**Description :**
This routine retrieves a free time RANGE from a schedule and returns a handle 
to the memory where the range has been placed. It will only return 64k of free 
time ranges.  Note: submitting a range or time that is in the past is not 
supported.
**Parameters :**
Input :
hCntnr  -  The handle to the container of the schedule.

hSchedObj  -  The HCNTNROBJ of the schedule project.

punidIgnore  -  Points to UNID to ignore in busy time calculation.

fFindFirstFit  -  If true then only the first fit is used

wDuration  -  Number of minutes in meeting if fFindFirstFit is True

Output :
(routine)  -  NOERROR - Successfully extracted free time range.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


pInterval  -  Points to where we return the overall interval of the schedule

retdwSize  -  The size of the range returned

rethRange  -  Points to where we return a handle to the time range associated with this schedule. Note: callers must free this when they're done.

**Sample Usage :**
```
	/* Get the first free time available */
 if (error = Schedule_ExtractFreeTimeRange(rethCntnr, hSchedObj, &theApptUnid, 
fFindFirstFit, wDuration, &pInterval, &retdwSize, &rethRange))
        LAPI_RETURN (ERR(error));
```
**See Also :**
[SchFreeTimeSearch](D:/md_files/SchFreeTimeSearch.md)
---
