##### Function : Database
##### NSFDbCreateExtended - Creates a new Domino database with additional options.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCreateExtended(

	const char far *PathName,
	WORD  DbClass,
	BOOL  ForceCreation,
	WORD  Options,
	BYTE  EncryptStrength,
	DWORD  MaxFileSize);
```
**Description :**

This function creates a new Domino database.  It provides added functionality 
to NSFDbCreate.

After creating a database, you must open it with NSFDbOpen or NSFDbOpenExtended 
before you can use it.

**Parameters :**
Input :
PathName  -  A pointer to the pathname of the database to be created.  

If the database will be in the default  data directory, you may omit the directory specifier.  If the database will have the filename extension ".NSF", you may omit the extension.  

If you are interested in creating a remote database on a particular Lotus Domino Server, use OSPathNetConstruct to build a fully qualified network pathname.  

Note:  Your ability to perform this function remotely can also be affected by a server's use of Server Access Groups and/or your lack of a common certificate.  If your local user name appears in the target server's notes.ini in a DENY_ACCESS= statement, you will not be allowed to create anything on that server.  If you do not share a common certificate, you will not be allowed to create anything on that server.

DbClass  -  Specifies the class of the database created.  See DB_CLASS for classes that may be specified.

ForceCreation  -  Controls whether the call will overwrite an existing database of the same name.  Set to TRUE to overwrite, set to FALSE not to overwrite.

Options  -  Database creation option flags.  See DBCREATE_xxx

EncryptStrength  -  Local encryption level for the database.  See DBCREATE_ENCRYPT_xxx.  Specify DBCREATE_LOCALSECURITY in order to create a locally encrypted database.  Otherwise, use DBCREATE_ENCRYPT_NONE for this parameter.

MaxFileSize  -  Optional.  Maximum file size of the database, in bytes.  In order to specify a maximum file size, use the database class, DBCLASS_BY_EXTENSION and use the option, DBCREATE_MAX_SPECIFIED.

Output :
(routine)  -  Return status from this call -- indicates either success, or what the error is.  The return codes include:

NOERROR
ERR_EXISTS - Database file already exists and the call specified not to overwrite an existing database.
ERR_DBCLASS - Invalid database class.
ERR_xxx - Errors returned by lower level functions.   Use OSLoadString to display/log a description of the error.



**See Also :**
[NSFDbCreate](/domino-c-api-docs/reference/Func/NSFDbCreate)
[OSPathNetConstruct](/domino-c-api-docs/reference/Func/OSPathNetConstruct)
[NSFDbOpen](/domino-c-api-docs/reference/Func/NSFDbOpen)
[DBCLASS_xxx](/domino-c-api-docs/reference/Symb/DBCLASS_xxx)
[DBCREATE_ENCRYPT_xxx](/domino-c-api-docs/reference/Symb/DBCREATE_ENCRYPT_xxx)
[DBCREATE_xxx](/domino-c-api-docs/reference/Symb/DBCREATE_xxx)
---
