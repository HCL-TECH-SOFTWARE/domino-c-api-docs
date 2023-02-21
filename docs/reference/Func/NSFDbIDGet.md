##### Function : Database
##### NSFDbIDGet - Get the database's ID (DBID).
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbIDGet(

	DBHANDLE  hDB,
	DBID far *retDbID);
```
**Description :**

This function obtains the database's ID or creation time/date.  This TIMEDATE 
structure is NOT normalized to Greenwich Mean Time, so it still contains both 
the local time zone and the daylight savings time settings for the time zone 
where the database was created.

**Parameters :**
Input :
hDB  -  A handle to a Domino database.

Output :
(routine)  -  Always returns NOERROR.


retDbID  -  The addres of a DBID or TIMEDATE structure in which the creation time/date of the database is returned.  Given that it is not GMT normalized and its base unit of storage is 10 milli-second intervals, this ID can be reliably used as a unique world-wide identifier of a particular copy or replica of a database.


**Sample Usage :**
```
/* Get the Database IDs */
NSFDbIDGet(db_handle_src, &database_id_src);
NSFDbIDGet(db_handle_dst, &database_id_dst);
```
**See Also :**
[NSFDbOpen](/domino-c-api-docs/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/domino-c-api-docs/reference/Func/NSFDbOpenExtended)
[OSCurrentTIMEDATE](/domino-c-api-docs/reference/Func/OSCurrentTIMEDATE)
---
