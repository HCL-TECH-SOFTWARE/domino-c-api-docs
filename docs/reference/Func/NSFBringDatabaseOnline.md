##### Function : Backup
##### NSFBringDatabaseOnline - Bring an offline database online.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFBringDatabaseOnline(

	const char far *dbPath,
	DWORD  options);
```
**Description :**

This function will bring a database online for access after it has been taken 
offline by NSFTakeDatabaseOffline.

**Parameters :**
Input :
dbPath  -  Path to the database to be brought online.

options  -  Reserved, must be zero

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.



**Sample Usage :**
```
   if (!(err = NSFBringDatabaseOnline(DbPath, 0)))
   {
      sprintf(EventString, "Database file %s brought online : ", DbPath);
      EventLog(LogFD, EventString);
   }
   else
   {
      sprintf(EventString,
              "*** ERROR bringing database %s online *** (%s) : ",
              DbPath,
              print_api_error(err));
      EventLog(LogFD, EventString);
   }

```
**See Also :**
[NSFTakeDatabaseOffline](/domino-c-api-docs/reference/Func/NSFTakeDatabaseOffline)
---
