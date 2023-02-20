##### Function : iCalendar
##### CalUpdateEntry - This will modify an existing calendar entry.
---
```
#include <calapi.h>
STATUS CalUpdateEntry(

	DBHANDLE  hDB,
	const char*pszCalEntry,
	const char*pszUID,
	const char*pszRecurID,
	const char*pszComments,
	DWORD  dwFlags,
	void*pCtx);
```
**Description :**

This will modify an existing calendar entry.  This supports either single 
entries or recurring entries, but recurring entries will only 
support updates for a single instance specified via RECURRENCE-ID that may not 
include a RANGE (This may be permitted in the future but 
for now will return an error).
The iCalendar input may only contain a single VEVENT and must contain a UID.
By default, attachments and custom data (for fields contained in $CSCopyItems) 
will be maintained from the
existing calendar entry.  Similarly, description will also be maintained if it 
is not specified in the iCalendar
content that is updating.  Both of these behaviors can be canceled via the 
CAL_WRITE_COMPLETE_REPLACE flag.
If the mailfile owner is the meeting organizer, appropriate notices will be 
sent out to meeting participants (unless
CAL_WRITE_DISABLE_IMPLICIT_SCHEDULING is specified)

**Parameters :**
Input :
hDB  -  The database containing the entry to update

pszCalEntry  -  The iCalendar data representing the updated entry

pszUID  -  If non-NULL, this value MUST match the UID value in the iCalendar input if present,or else this returns ERR_InvalidVEventPropertyFound.  If the iCalendar input has no UID this value will be used.

pszRecurID  -  If non-NULL, this value MUST match the RECURRENCE-ID value in the iCalendar input if present, or else this returns ERR_InvalidVEventPropertyFound.  If the iCalendar input has no RECURRENCE-ID this value will be used.

pszComments  -  If non-NULL, this text will be sent as comments on any notices sent to meeting participants as a result of this call. that will be included on the notices. Can be NULL.

dwFlags  -  CAL_WRITE_xxx flags to control non-default behavior. Supported: CAL_WRITE_MODIFY_LITERAL, CAL_WRITE_DISABLE_IMPLICIT_SCHEDULING, CAL_WRITE_IGNORE_VERIFY_DB.

pCtx  -  RESERVED - MUST be NULL

Output :
(routine)  -  status of updating entry
		NOERROR on success
		ERR_NULL_DBHANDLE			The database handle is NULL
		ERR_MISC_INVALID_ARGS		Unexpected arguments provided
		ERR_CALACTION_INVALID		This calendar entry is not in a state where updating it is supported.
		ERR_NO_CALENDAR_FOUND		Unable to find the entry because the required view does not exist in this database
		ERR_NOT_FOUND				There are no entries that match the specified UID or UID/recurid in the database
		ERR_NOT_YET_IMPLEMENTED	This update is not yet supported (update range or multiple VEVENTs?)
		ERR_CS_PROFILE_NOOWNER	Calendar Profile does not specify owner
		ERR_UNEXPECTED_METHOD		Provided iCalendar contains a method (no method expected here)
		ERR_ICAL2NOTE_OUTOFDATE	iCalendar input is out of date in regards to sequence information.
		ERR_MissingVEventComponents		Missing required VEvent components
		ERR_InvalidVEventPropertyFound	Invalid VEvent property found
		ERR_ICAL2NOTE_CONVERT		Error interpereting iCalendar input
		ERR_MISC_UNEXPECTED_ERROR	Unexpected internal error
		ERR_IMPLICIT_SCHED_FAILED	Entry was updated, but errors were encountered sending notices to meeting participants



**See Also :**
[CalCreateEntry](/reference/Func/CalCreateEntry)
[CalReadEntry](/reference/Func/CalReadEntry)
---
