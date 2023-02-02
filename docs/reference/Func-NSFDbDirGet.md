##### Function : Database
##### NSFDbDirGet - Get the database directory.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbDirGet(**

	DBHANDLE  hDB,
	char *retDir);
**Description :**
This function gets the path to the database directory, without the database 
name, relative to the Domino data directory.
**Parameters :**
Input :
hDB  -  Handle to a database.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully got the path to the database directory.


retDir  -  Pointer to a buffer in which the path of the database directory, relative to the Domino data directory, associated with hDB is returned.  Declared buffer must be at least MAXPATH characters in length.

**See Also :**
[](D:/md_files/.md)
---
