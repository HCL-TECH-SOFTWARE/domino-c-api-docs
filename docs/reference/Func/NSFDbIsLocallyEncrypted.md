##### Function : Database
##### NSFDbIsLocallyEncrypted - Check to see if database is locally encrypted.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbIsLocallyEncrypted(

	DBHANDLE  hDB,
	BOOL *pRetval);
```
**Description :**

Check to see if database is locally encrypted.

**Parameters :**
Input :
hDB  -  Handle to database.

Output :
(routine)  -  Return status from this call -- indicates either success (NOERROR) or what the error is. 


pRetval  -  If TRUE, database is locally encrypted.


**See Also :**
---
