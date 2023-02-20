##### Function : Database
##### NSFDbClassGet - Gets the database creation class.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbClassGet(

	HANDLE  hDB,
	WORD far *retClass);
```
**Description :**

This function gets the database creation class specified when the database was 
created.  This function is useful for those API programs that need to determine 
whether the database was created specifically for alternate mail (in this case, 
DBCLASS_ENCAPSMAILFILE will be returned).  However, for all other types of 
databases, there is no guarantee that the database matches the database 
creation class description.

**Parameters :**
Input :
hDB  -  Handle to an opened Domino database.

Output :
(routine)  -  Return status from this call.  NOERROR is always returned.


retClass  -  The address of the database creation class specified when the database was created.  See DBCLASS_xxx for a list of the database creation classes.


**See Also :**
[NSFDbCreate](/reference/Func/NSFDbCreate)
[DBCLASS_xxx](/reference/Symb/DBCLASS_xxx)
---
