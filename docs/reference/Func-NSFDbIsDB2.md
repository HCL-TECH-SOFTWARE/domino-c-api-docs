##### Function : Backup
##### NSFDbIsDB2 - Determines whether a Domino database is a DB2 database or an NSF database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbIsDB2(**

	DBHANDLE  hDb,
	BOOL &  isDB2);
**Description :**
This function determines whether a Domino database is a DB2 database or an NSF 
database.
**Parameters :**
Input :
hDb  -  A handle to an open Notes database.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successful.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


isDB2  -  TRUE if this Domino database is a DB2 database.  FALSE if this Domino database is an NSF database.

**See Also :**
[](D:/md_files/.md)
---
