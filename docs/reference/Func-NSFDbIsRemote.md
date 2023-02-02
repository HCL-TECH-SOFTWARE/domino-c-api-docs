##### Function : Database
##### NSFDbIsRemote - Check whether a database is remote or local.
---
##### #include <nsfdb.h>
BOOL **NSFDbIsRemote(**

	DBHANDLE  hdb);
**Description :**
Check whether a database is on a remote or local server. NULLHANDLE indicates a 
local database.
**Parameters :**
Input :
hdb  -  An open DB handle.

Output :
(routine)  -  Returns TRUE, if database is on a remote server. 
                 FALSE, if database is on a local server.


**Sample Usage :**
```
	/* hDB is handle to database. */ 
	if (NSFDbIsRemote(hDB))
	{
   printf("Database is remote."); 
	} 
	else
  { 
	 printf("Database is local."); 
  }
```
**See Also :**
[](D:/md_files/.md)
---
