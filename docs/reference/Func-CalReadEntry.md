##### Function : iCalendar
##### CalReadEntry - This will return complete iCalendar data for the specified entry.
---
##### #include <calapi.h>
STATUS **CalReadEntry(**

	DBHANDLE  hDB,
	const char*pszUID,
	const char*pszRecurID,
	MEMHANDLE far *hRetCalData,
	DWORD*pdwReserved,
	DWORD  dwFlags,
	void*pCtx);
**Description :**
This will return complete iCalendar data for the specified entry.  
For recurring entries, this may result in multiple VEVENTs in the returned 
iCalendar data.  In this case, the first VEVENT represents the recurrence set 
and additional entries represent exceptions to the recurrence set.
All instances that differ from the recurrence set will be returned as 
additional VEVENTs containing the exceptional data. There is no concept of 
'runs' of instances or RANGE of instances.
Alternatively, a specific instance may be requested using pszRecurID and only 
the data for that instance will be returned.
Returned data will not include rich text description.
All participants of a meeting will be returned as PARTSTAT=NEEDS-ACTION even if 
they have responded.
**Parameters :**
Input :
hDB  -  The database from which entries are returned.

pszUID  -  The UID of the entry to be returned.

pszRecurID  -  NULL for single entries or to read data for an entire recurring series.If populated, this is the RECURRENCE-ID of the specific instance to read.

pdwReserved  -  RESERVED - MUST be NULL

dwFlags  -  CAL_READ_xxx flags to control non-default behavior

pCtx  -  RESERVED - MUST be NULL

Output :
(routine)  -  status of read entry
		NOERROR on success
		ERR_NULL_DBHANDLE			The database handle is NULL
		ERR_MISC_INVALID_ARGS		Unexpected arguments provided
		ERR_TDI_CONV				The recurrence ID specified cannot be interpreted
		ERR_NO_CALENDAR_FOUND		Unable to find the entry because the required view does not exist in this database
		ERR_NOT_FOUND				There are no entries that match the specified UID or UID/recurid in the database
		ERR_NOTE2ICAL_CONVERT		Unable to convert to iCalendar
		ERR_MISC_UNEXPECTED_ERROR	Unexpected internal error


hRetCalData  -  Handle to the returned iCalendar data.  It is the caller's responsibility to free this memory.

**See Also :**
[](D:/md_files/.md)
---
