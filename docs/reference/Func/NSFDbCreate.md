##### Function : Database
##### NSFDbCreate - Creates a new Domino database.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCreate(

	const char far *PathName,
	USHORT  DbClass,
	BOOL  ForceCreation);
```
**Description :**

This function creates a new Domino database.  You also may control whether the 
call will overwrite an existing database of the same name and the database 
class.

The newly created database is completely empty.  It has no title, no access 
control list, no icon, no forms, no views, and no documents.  Also, the 
database is closed.  After creating a database, you must open it with NSFDbOpen 
or NSFDbOpenExtended before you can begin to copy/create the various elements 
of this new database.

**Parameters :**
Input :
PathName  -  A pointer to the pathname of the database to be created.  

If the database will be in the default  data directory, you may omit the directory specifier. If the database will have the filename extension ".NSF", you may omit the extension.  

If you are interested in creating a remote database on a particular Lotus Domino Server, OSPathNetConstruct will allow you to build a fully qualified network pathname.  

Note:  Your ability to perform this function remotely is subject to the access rights you have to that server.  Access rights to a server is controlled by the server's use of Server Access Groups, proper certification in your ID file and the Restrictions section of the server document in the server's Domino Directory. 

DbClass  -  Specifies the class of the database created.  Almost always specified as DBCLASS_NOTEFILE.  See DBCLASS_xxx for other classes that may be specified.

ForceCreation  -  Controls whether the call will overwrite an existing database of the same name.  Set to TRUE to overwrite, set to FALSE not to overwrite.

Output :
(routine)  -  Return status from this call -- indicates either success, or what the error is.  The return codes include:

NOERROR - Success.
ERR_EXISTS - ForceCreation parameter set to FALSE and file to be created already exists.
ERR_DBCLASS - Invalid database class.



**Sample Usage :**
```
/* Create destination database */

if (error = NSFDbCreate (output_path, DBCLASS_NOTEFILE, FALSE))
{
     /* Close previously opened database */
  NSFDbClose (input_handle);
  API_RETURN (ERR(error));
}
```
**See Also :**
[OSPathNetConstruct](/reference/Func/OSPathNetConstruct)
[NSFDbOpen](/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/reference/Func/NSFDbOpenExtended)
[DBCLASS_xxx](/reference/Symb/DBCLASS_xxx)
---
