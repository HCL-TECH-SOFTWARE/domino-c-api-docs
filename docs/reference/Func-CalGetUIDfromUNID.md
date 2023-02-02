##### Function : iCalendar
##### CalGetUIDfromUNID - This is a convinience method that returns a UID from a UNID.
---
##### #include <calapi.h>
STATUS **CalGetUIDfromUNID(**

	DBHANDLE  hDB,
	UNID  unid,
	char*pszUID,
	WORD  wLen,
	void*pReserved,
	DWORD  dwFlags,
	void*pCtx);
**Description :**
This is a convinience method that returns a UID from a UNID.  UNID->UID is a 
many to one mapping since one or several notes may represent a calendar entry 
(especially if it repeats) and its related notices.
As such, the UID output will be the same for all notes that refer to the same 
calendar entry.
This method may incur a note open, so there could be performance impact.
**Parameters :**
Input :
hDB  -  The database containing the note referenced by unid.

unid  -  UNID of a calendar note.

wLen  -  Length of pszRetUID buffer (reccomended to be at least 64).

pReserved  -  RESERVED - MUST be NULL.

dwFlags  -  Flags - none currently.

pCtx  -  RESERVED - MUST be NULL.

Output :
(routine)  -  NOERROR on success
ERR_NULL_DBHANDLE			The database handle is NULL
ERR_INVALID_NOTE			Note is not valid or is not a calendar note
ERR_MISC_INVALID_ARGS		Unexpected arguments provided
ERR_VALUE_LENGTH			The value is too long for the allocated buffer


pszUID  -  

**See Also :**
[](D:/md_files/.md)
---
