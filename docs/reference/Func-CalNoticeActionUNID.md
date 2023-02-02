##### Function : iCalendar
##### CalNoticeActionUNID - Same as CalNoticeAction but takes a UNID input instead of a NOTEID input.
---
##### #include <calapi.h>
STATUS **CalNoticeActionUNID(**

	DBHANDLE  hDB,
	UNID  unid,
	DWORD  dwAction,
	const char*pszComments,
	PEXT_CALACTION_DATA  pExtActionInfo,
	DWORD  dwFlags,
	void*pCtx);
**Description :**

**Parameters :**
Input :
hDB  -  The database containing the notice to act on.

unid  -  The UNID of the notice to act on

dwAction  -  The action to perform as defined in CAL_PROCESS_xxx values.

pszComments  -  Comments to include on the outgoing notice(s) to organizer or participants (can be NULL).

pExtActionInfo  -  Conveys any additional information required to perform dwAction - NULL for actions that do not require additional information to perform, required for CAL_PROCESS_DELEGATE and CAL_PROCESS_COUNTER.

dwFlags  -  Flags - (a CAL_ACTION _xxx value).

pCtx  -  RESERVED - MUST be NULL.


**See Also :**
[](D:/md_files/.md)
---
