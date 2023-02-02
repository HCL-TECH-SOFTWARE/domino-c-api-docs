##### Function : Database
##### NSFDB2GetInfo - Gets the DB2 database information buffer.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDB2GetInfo(**

	DBHANDLE  hDB,
	int  infotype,
	void far *buffer,
	DWORD *size);
**Description :**
This function retrieves the DB2-related information about a Domino database.
**Parameters :**
Input :
hDB  -  The handle to the database for which you want information.

infotype  -  The type of information to return.  See DB2NSF_INFO_xxx.

size  -  Specifies the size, in bytes, of buffer.

Output :
(routine)  -  Return status from this call indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_DB2NSF_BUF_TOO_SMALL - Allocated buffer too small.

ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error code for display.


buffer  -  Pointer to a buffer where specific database information will be returned.  For type of database information returned, see DB2NSF_INFO_xxx.

size  -  The size, in bytes, of the data returned.  If STATUS is ERR_DB2NSF_BUF_TOO_SMALL, returns the required size, in bytes, of the buffer.

**See Also :**
[DB2NSF_INFO_xxx](D:/md_files/DB2NSF_INFO_xxx.md)
[NSFDB2GetServerInfo](D:/md_files/NSFDB2GetServerInfo.md)
[NSFDB2ListNSFDB2Databases](D:/md_files/NSFDB2ListNSFDB2Databases.md)
[NSFDB2ReconnectNotesDatabase](D:/md_files/NSFDB2ReconnectNotesDatabase.md)
[NSFDB2RegenerateLinks](D:/md_files/NSFDB2RegenerateLinks.md)
---
