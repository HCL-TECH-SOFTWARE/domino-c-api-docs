##### Function : Database
##### NSFDbPathIsRemote - Determine whether a database is remote or local based on its path.
---
```
#include <nsfdb.h>
Boolean NSFDbPathIsRemote(

	char *file name);
```
**Description :**

Determine whether a database is remote or local based on its path.

**Parameters :**
Input :
file name  -  Server, path, and file name of database.

Output :
(routine)  -  TRUE - if the database is remote (by path name). 

   FALSE - if the database is local (by path name).



**Sample Usage :**
```
	/* Make sure the database is local. */ 
	char Pathname[MAXPATH] = "servername!!dbpath\db.nsf"; 

	if (NSFDbPathIsRemote(Pathname))
   return NOERROR;
```
**See Also :**
---
