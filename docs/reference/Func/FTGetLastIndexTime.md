##### Function : Full Text Search
##### FTGetLastIndexTime - Returns the last time a database was full text indexed.
---
```
#include <ft.h>
STATUS LNPUBLIC FTGetLastIndexTime(

	DBHANDLE  hDB,
	TIMEDATE far *retTime);
```
**Description :**

This routine returns the last time a database was full text indexed.  It can 
also be used to determine if a database is full text indexed.  If the database 
is not full text indexed, ERR_FT_NOT_INDEXED is returned.


**Parameters :**
Input :
hDB  -  The handle to the open database.

Output :
(routine)  -   Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_FT_NOT_INDEXED - Database is not full text indexed.

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret the code.


retTime  -  Pointer to returned TimeDate of last index operation.


**See Also :**
[FTIndex](/reference/Func/FTIndex)
---
