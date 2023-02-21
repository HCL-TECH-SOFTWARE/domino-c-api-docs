##### Function : Database
##### NSFDbAccessGet - Get the current access level for an open database.
---
```
#include <nsfdb.h>
void LNPUBLIC NSFDbAccessGet(

	DBHANDLE  hDB,
	WORD far *retAccessLevel,
	WORD far *retAccessFlag);
```
**Description :**

This function gets the level of database access granted to the username that 
opened the database.

**Parameters :**
Input :
hDB  -  The handle to the open database.

Output :
(routine)  -  None


retAccessLevel  -  The level of database access (as in ACL_LEVEL_xxx) that is allowed to the username that was used to open the database.

retAccessFlag  -  Modifier flags (as in ACL_FLAG_xxx) for the user's database access.


**See Also :**
[ACL_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACL_FLAG_xxx)
[ACL_LEVEL_xxx](/domino-c-api-docs/reference/Symb/ACL_LEVEL_xxx)
---
