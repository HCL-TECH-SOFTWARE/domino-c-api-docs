##### Function : iCalendar
##### CalReadNoticeUNID - Same as CalReadNotice but takes a UNID input instead of a NOTEID input.
---
```
#include <calapi.h>
STATUS CalReadNoticeUNID(

	DBHANDLE  hDB,
	UNID  unid,
	MEMHANDLE far *hRetCalData,
	void*pReserved,
	DWORD  dwFlags,
	void*pCtx);
```
**Description :**



**Parameters :**
Input :
hDB  -  The database from which entries are returned.

unid  -  The UNID of the notice to be returned.

pReserved  -  RESERVED - MUST be NULL.

dwFlags  -  CAL_READ_xxx flags to control non-default behavior. Supported: CAL_READ_HIDE_X_LOTUS, CAL_READ_INCLUDE_X_LOTUS.

pCtx  -  RESERVED - MUST be NULL.

Output :
hRetCalData  -  


**See Also :**
---
