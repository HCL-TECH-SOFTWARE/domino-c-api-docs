##### Function : iCalendar
##### CalGetUIDfromNOTEID - This is a convinience method that returns a UID from a NOTEID.
---
##### #include <calapi.h>
STATUS **CalGetUIDfromNOTEID(**

	DBHANDLE  hDB,
	NOTEID  noteid,
	char*pszUID,
	WORD  wLen,
	void*pReserved,
	DWORD  dwFlags,
	void*pCtx);
**Description :**
This is a convinience method that returns a UID from a NOTEID.  NOTEID->UID is 
a many to one mapping since one or several notes may represent a calendar entry 
(especially if it repeats) and its related notices.
As such, the UID output will be the same for all notes that refer to the same 
calendar entry.
This method may incur a note open, so there could be performance impact.
**Parameters :**
Input :
hDB  -  The database containing the note referenced by noteid.

noteid  -  NOTEID of a calendar note.

wLen  -  Length of pszRetUID buffer(reccomended to be at least 64).

pReserved  -  RESERVED - MUST be NULL.

dwFlags  -  Flags - none currently.

pCtx  -  RESERVED - MUST be NULL.

Output :
(routine)  -  NOERROR on success
ERR_NULL_DBHANDLE			The database handle is NULL
ERR_INVALID_NOTE			Note is not valid or is not a calendar note
ERR_MISC_INVALID_ARGS		Unexpected arguments provided
ERR_VALUE_LENGTH			The value is too long for the allocated buffer


pszUID  -  Buffer to populate with the UID.

**See Also :**
[](D:/md_files/.md)
---
