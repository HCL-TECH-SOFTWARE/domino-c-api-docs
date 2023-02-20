##### Function : Access Control List
##### NSFDbHasFullAccess - Check whether the database handle has full access to the database.
---
```
#include <nsfdb.h>
FLAG NSFDbHasFullAccess(

	DBHANDLE  hdb);
```
**Description :**

Check whether the database handle has full access to perform operations on a 
database. Full access is Read, Write, and Edit access as well as the ability to:

Monitor the database.
Replicate the database.
Delete notes from the database.
Delete the database.
Store private folders in the database.

**Parameters :**
Input :
hdb  -  It is an open DB handle.

Output :
(routine)  -  Returns TRUE if a the database handle has full access to a database, else returns FALSE.



**Sample Usage :**
```
	/* Check DB has full access. */ 
	DBHANDLE hdb; 

	NSFDBOpen(<database path>, &hdb); 
	if(NSFDbHasFullAccess(hDB)) 
	{ 
	 printf("Can perform operation that require full access."); 
	} 
	else 
            { 
	 printf("Cannot perform operations that requires full access."); 
	}
```
**See Also :**
---
