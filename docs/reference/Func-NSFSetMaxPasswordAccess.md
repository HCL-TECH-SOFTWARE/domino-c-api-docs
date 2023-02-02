##### Function : Access Control List
##### NSFSetMaxPasswordAccess - Sets the maximum internet name and password access level.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFSetMaxPasswordAccess(**

	DBHANDLE  hDB,
	WORD  Level);
**Description :**
Set the database's maximum internet name and password access level for Web 
users.
**Parameters :**
Input :
hDB  -  Handle to database.

Level  -  Maximum password access level (ACL_LEVEL_xxx).

Output :
(routine)  -  NOERROR - Successfully set the password access level.
ERR_ACL_VERSION - Invalid Level parameter.
ERR_xxx - Use OSLoadString to display the error returned.


**See Also :**
[ACL_LEVEL_xxx](D:/md_files/ACL_LEVEL_xxx.md)
[NSFGetMaxPasswordAccess](D:/md_files/NSFGetMaxPasswordAccess.md)
---
