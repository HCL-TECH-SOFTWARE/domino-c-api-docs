##### Function : iCalendar
##### CalNoticeAction - Process a calendar notice.
---
##### #include <calapi.h>
STATUS **CalNoticeAction(**

	DBHANDLE  hDB,
	NOTEID  noteID,
	DWORD  dwAction,
	const char*pszComments,
	PEXT_CALACTION_DATA  pExtActionInfo,
	DWORD  dwFlags,
	void*pCtx);
**Description :**
Process a calendar notice. This makes the appropriate modifications to the 
calendar entry and also sends appropriate notices out.
**Parameters :**
Input :
hDB  -  The database containing the notice to act on.

noteID  -  The noteid of the notice to act on.

dwAction  -  The action to perform as defined in CAL_PROCESS_xxx values.

pszComments  -  Comments to include on the outgoing notice(s) to organizer or participants (can be NULL).

pExtActionInfo  -  Conveys any additional information required to perform dwAction - NULL for actions that do not require additional information to perform, required for CAL_PROCESS_DELEGATE and CAL_PROCESS_COUNTER.

dwFlags  -  Flags - (a CAL_ACTION _xxx value).

pCtx  -  RESERVED - MUST be NULL.


**See Also :**
[](D:/md_files/.md)
---
