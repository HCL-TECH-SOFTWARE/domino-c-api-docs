##### Function : Database
##### NSFDB2GetServerInfo - Gets the DB2-related information about a Domino server.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDB2GetServerInfo(

	char *szServerName,
	int  infotype,
	void far *buffer,
	DWORD *size);
```
**Description :**

This function retrieves the DB2-related information about a Domino server.

**Parameters :**
Input :
szServerName  -  The name of the Domino server.

infotype  -  The type of information to return.  See DB2NSF_SERVINFO_xxx.

size  -  Specifies the size, in bytes, of buffer.

Output :
(routine)  -  Return status from this call indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_DB2NSF_BUF_TOO_SMALL - Allocated buffer too small.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


buffer  -  Pointer to a buffer where specific server information will be returned.  For type of server information returned, see DB2NSF_SERVERINFO_xxx.

size  -  The size, in bytes, of the data returned.  If STATUS is ERR_DB2NSF_BUF_TOO_SMALL, returns the required size, in bytes, of the buffer.


**See Also :**
[DB2NSF_SERVINFO_xxx](/domino-c-api-docs/reference/Symb/DB2NSF_SERVINFO_xxx)
[NSFDB2GetInfo](/domino-c-api-docs/reference/Func/NSFDB2GetInfo)
[NSFDB2ListNSFDB2Databases](/domino-c-api-docs/reference/Func/NSFDB2ListNSFDB2Databases)
[NSFDB2ReconnectNotesDatabase](/domino-c-api-docs/reference/Func/NSFDB2ReconnectNotesDatabase)
[NSFDB2RegenerateLinks](/domino-c-api-docs/reference/Func/NSFDB2RegenerateLinks)
---
