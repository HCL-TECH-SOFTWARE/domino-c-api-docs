##### Function : iCalendar
##### CalOpenNoteHandle - This is a method to get a note handle for an entry on the calendar.
---
```
#include <calapi.h>
STATUS CalOpenNoteHandle(

	DBHANDLE  hDB,
	const char*pszUID,
	const char*pszRecurID,
	NOTEHANDLE far *rethNote,
	DWORD  dwFlags,
	void*pCtx);
```
**Description :**

This is a method to get a note handle for an entry on the calendar.
The intent is that the note handle can be used to get information about an 
entry or instance or to write additional information to the entry or instance 
(beyond what is defined in iCalendar and/or available in this API).
It is the callers responsibility to close the note via NSFNoteClose.
When opening a recurring entry, a valid recurrence ID MUST also be provided.  A 
note representing the single instance will be returned.
This might cause notes to be created or modified as a side effect.

**Parameters :**
Input :
hDB  -  The database containing the entry to open.

pszUID  -  The UID of the entry to get a note handle for.

pszRecurID  -  The RECURRENCE-ID of the instance to get a note handle for.  Timezones not permitted (time values must be in UTC time). NULL for single entries.  Must be present for recurring entries.

dwFlags  -  CAL_NOTEOPEN_xxx flags to control non-default behavior. Supported: CAL_NOTEOPEN_HANDLE_NOSPLIT.

pCtx  -  RESERVED - MUST be NULL.

Output :
(routine)  -  NOERROR on success
ERR_NULL_DBHANDLE			The database handle is NULL
ERR_NO_CALENDAR_FOUND		Unable to find the entry because the required view does not exist in this database
ERR_NOT_FOUND				There are no entries that match the specified UID or UID/recurid in the database
ERR_MISC_INVALID_ARGS		Unexpected arguments provided
ERR_TDI_CONV				The recurrence ID specified cannot be interpreted
ERR_MISC_UNEXPECTED_ERROR	Unexpected internal error


rethNote  -  The returned open note handle of the calendar entry.


**See Also :**
---
