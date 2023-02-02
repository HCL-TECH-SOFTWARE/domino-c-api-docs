##### Function : Database
##### NSFGetAllFolderChanges - Get all folder changes.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFGetAllFolderChanges(**

	DHANDLE  hViewDB,
	DHANDLE  hDataDB,
	TIMEDATE *Since,
	DWORD  Flags,
	NSFGETALLFOLDERCHANGESCALLBACK  Callback,
	void *Param,
	TIMEDATE *Until);
**Description :**
This function will get all folder changes for a specific time period and call 
the callback routine for each change.
**Parameters :**
Input :
hViewDB  -  Handle of the database that contains the folders.

hDataDB  -  Handle to the database that contains the data notes.  This must reference the same database as hViewDB.

Since  -  A pointer to a TIMEDATE structure containing a time/date value specifying the earliest time the folder was modified.

Flags  -  Flags.

Callback  -  The get all folder changes callback function pointer.  This function is called for each folder change.  See NSFGETALLFOLDERCHANGESCALLBACK.

Param  -  Callback parameter.  See NSFGETALLFOLDERCHANGESCALLBACK.

Until  -  A pointer to a TIMEDATE structure containing a time/date value specifying the latest time the folder was modified.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.


**See Also :**
[NSFGETALLFOLDERCHANGESCALLBACK](D:/md_files/NSFGETALLFOLDERCHANGESCALLBACK.md)
---
