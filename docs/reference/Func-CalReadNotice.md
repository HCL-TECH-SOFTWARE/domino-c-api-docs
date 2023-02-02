##### Function : iCalendar
##### CalReadNotice - This will return iCalendar data representing a notice with the specified NOTIED.
---
##### #include <calapi.h>
STATUS **CalReadNotice(**

	DBHANDLE  hDB,
	NOTEID  noteID,
	MEMHANDLE far *hRetCalData,
	void*pReserved,
	DWORD  dwFlags,
	void*pCtx);
**Description :**
This will return iCalendar data representing a notice with the specified 
NOTIED.  A notice may not yet be applied to the calendar entries itself, but an 
application may want to read the notice (and process it).  Examples of notices 
include invitations, reschedules, information updates, confirmations, 
cancelations, counterproposals, requests for information, acceptances, 
declines, tenative acceptances, etc.
**Parameters :**
Input :
hDB  -  The database from which entries are returned.

noteID  -  The NOTEID of the notice to be returned.

pReserved  -  RESERVED - MUST be NULL.

dwFlags  -  CAL_READ_xxx flags to control non-default behavior. Supported: CAL_READ_HIDE_X_LOTUS, CAL_READ_INCLUDE_X_LOTUS.

pCtx  -  RESERVED - MUST be NULL.

Output :
hRetCalData  -  

**See Also :**
[](D:/md_files/.md)
---
