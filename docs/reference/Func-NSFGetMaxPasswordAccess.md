##### Function : Access Control List
##### NSFGetMaxPasswordAccess - Returns the maximum internet name and password access level.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFGetMaxPasswordAccess(**

	DBHANDLE  hDB,
	WORD *retLevel);
**Description :**
Returns the database's maximum internet name and password access level for Web 
users.
**Parameters :**
Input :
hDB  -  Handle to database.

Output :
(routine)  -  NOERROR - Successfully returned the maximum access level of the user.
ERR_xxx - Use OSLoadString to display the error returned.


retLevel  -  Returns the database's maximum internet name and password access level (ACL_LEVEL_xxx).  

**See Also :**
[ACL_LEVEL_xxx](D:/md_files/ACL_LEVEL_xxx.md)
[NSFSetMaxPasswordAccess](D:/md_files/NSFSetMaxPasswordAccess.md)
---
