##### Function : Backup
##### NSFTakeDatabaseOffline - Take a database offline to allow recovery.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFTakeDatabaseOffline(**

	const char far *dbPath,
	DWORD  WaitTime,
	DWORD  options);
**Description :**
This function will stop access to a database and delete the database so that it 
can be recovered.
**Parameters :**
Input :
dbPath  -  Full path to the database to be taken offline.

WaitTime  -  Time to wait, in milliseconds, if the database cannot be taken offline immediately.

options  -  Zero to stop access to a database and delete the database so that it can be recovered.  See OFFLINE_xxx for more options.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_DBINUSE - Database is being accessed by one or more processes and cannot be taken offline.

ERR_xxx - Errors returned by lower level Notes functions.  Call to OSLoadString to interpret the error code for display.


**Sample Usage :**
```
   if (!(err = NSFTakeDatabaseOffline(DbPath, WaitTime, 0)))
   {
      sprintf(EventString, "Database file %s taken offline : ", DbPath);
      EventLog(LogFD, EventString);
   }
   else
   {
      sprintf(EventString,
              "*** ERROR taking database %s offline *** (%s) : ",
              DbPath,
              print_api_error(err));
      EventLog(LogFD, EventString);
   }

```
**See Also :**
[NSFBringDatabaseOnline](D:/md_files/NSFBringDatabaseOnline.md)
[OFFLINE_xxx](D:/md_files/OFFLINE_xxx.md)
---
