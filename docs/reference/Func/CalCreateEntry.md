##### Function : iCalendar
##### CalCreateEntry - Creates a calendar entry.
---
```
#include <calapi.h>
STATUS CalCreateEntry(

	DBHANDLE  hDB,
	const char*pszCalEntry,
	DWORD  dwFlags,
	MEMHANDLE*hRetUID,
	void*pCtx);
```
**Description :**

Creates a calendar entry.  This supports either a single entry, or a recurring 
entry which may contain multiple VEVENTS represenging both the series and 
exception data.The iCalendar input must only contain data for a single UID.For 
meetings, ATTENDEE PARTSTAT data is ignored.If the mailfile owner is the 
meeting organizer, invitations will be sent out to meeting participants (unless 
CAL_WRITE_DISABLE_IMPLICIT_SCHEDULING is specified)


**Parameters :**
Input :
hDB  -  The database where the entry will be created.

pszCalEntry  -  The iCalendar data representing the entry to create

dwFlags  -  CAL_WRITE_xxx flags to control non-default behavior

pCtx  -  RESERVED - MUST be NULL

Output :
(routine)  -  status of create entry
		NOERROR on success
		ERR_NULL_DBHANDLE			The database handle is NULL
		ERR_MISC_INVALID_ARGS		Unexpected arguments provided
		ERR_NO_CALENDAR_FOUND		Unable to find the entry because the required view does not exist in this database
		ERR_EXISTS				An entry already exists
		ERR_CS_PROFILE_NOOWNER	Calendar Profile does not specify owner
		ERR_UNEXPECTED_METHOD		Provided iCalendar contains a method (no method expected here)
		ERR_MissingVEventComponents		Missing required VEvent components
		ERR_InvalidVEventPropertyFound	Invalid VEvent property found, such as mismatched UIDs
		ERR_ICAL2NOTE_CONVERT		Error interpereting iCalendar input
		ERR_MISC_UNEXPECTED_ERROR	Unexpected internal error
		ERR_IMPLICIT_SCHED_FAILED	Entry created, but errors were encountered sending notices to meeting participants


hRetUID  -  If non-null, the UID of the created iCalendar will be placed here


**See Also :**
[CalReadEntry](/domino-c-api-docs/reference/Func/CalReadEntry)
---
