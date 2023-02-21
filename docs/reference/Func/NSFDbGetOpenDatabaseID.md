##### Function : Database
##### NSFDbGetOpenDatabaseID - Get a unique ID for an open database.
---
```
#include <nsfdb.h>
DWORD LNPUBLIC NSFDbGetOpenDatabaseID(

	DBHANDLE  hDBU);
```
**Description :**

Returns a unique 32-bit identifier for a database that is valid as long as any 
handle to the database remains open.  The same identifier will be returned for 
all handles that refer to the same database.  In particular, if NSFDbReopen() 
is called, a new handle will be created for the database, but this identifer 
will remain the same, providing a simple and efficient way to determine whether 
or not two database handles refer to the same database.

After all handles to the database have been closed and the database is opened, 
this function may or may not return a different database identifier.

**Parameters :**
Input :
hDBU  -  Handle to an open database.

Output :
(routine)  -  Open database ID.



**See Also :**
[NSFDbClose](/domino-c-api-docs/reference/Func/NSFDbClose)
[NSFDbOpen](/domino-c-api-docs/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/domino-c-api-docs/reference/Func/NSFDbOpenExtended)
[NSFDbReopen](/domino-c-api-docs/reference/Func/NSFDbReopen)
---
