##### Function : Database
##### NSFDbCreateExtendedWithOptions - Creates a new Domino NSF or DB2 database with additional options.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCreateExtendedWithOptions(

	const char far *filename,
	WORD  dbclass,
	BOOL  force,
	WORD  Option,
	DWORD  Option2,
	BYTE  EncryptStrength,
	DWORD  MaxFileSize,
	const char far *String1,
	const char far *String2,
	WORD  ReservedListLength,
	WORD  ReservedListCount,
	DHANDLE  hReservedList);
```
**Description :**

This function creates a new Domino NSF or DB2 database.  It provides added 
functionality to NSFDbCreateExtended.

After creating a database, you must open it with NSFDbOpen or NSFDbOpenExtended 
before you can use it.

**Parameters :**
Input :
filename  -  A pointer to the pathname of the database to be created.  

If the database will be in the default  data directory, you may omit the directory specifier.  If the database will have the filename extension ".NSF", you may omit the extension.  

If you are interested in creating a remote database on a particular Lotus Domino Server, use OSPathNetConstruct to build a fully qualified network pathname.  

Note:  Your ability to perform this function remotely can also be affected by a server's use of Server Access Groups and/or your lack of a common certificate.  If your local user name appears in the target server's notes.ini in a DENY_ACCESS= statement, you will not be allowed to create anything on that server.  If you do not share a common certificate, you will not be allowed to create anything on that server.

dbclass  -  Specifies the class of the database created.  See DB_CLASS for classes that may be specified.

force  -  Controls whether the call will overwrite an existing database of the same name.  Set to TRUE to overwrite, set to FALSE not to overwrite.

Option  -  Database creation option flags.  See DBCREATE_xxx

Option2  -  Database creation option flags.  See DBCREATE_xxx(2)

EncryptStrength  -  Local encryption level for the database.  See DBCREATE_ENCRYPT_xxx.  Specify DBCREATE_LOCALSECURITY in order to create a locally encrypted database.  Otherwise, use DBCREATE_ENCRYPT_NONE for this parameter.

MaxFileSize  -  Optional.  Maximum file size of the database, in bytes.  In order to specify a maximum file size, use the database class, DBCLASS_BY_EXTENSION and use the option, DBCREATE_MAX_SPECIFIED.

String1  -  Reserved for future use.

String2  -  Reserved for future use.

ReservedListLength  -  Reserved for future use.

ReservedListCount  -  Reserved for future use.

hReservedList  -  Reserved for future use.

Output :
(routine)  -  Return status from this call -- indicates either success, or what the error is.  The return codes include:

NOERROR
ERR_EXISTS - Database file already exists and the call specified not to overwrite an existing database.
ERR_DBCLASS - Invalid database class.
ERR_DB2NSF_CANNOT_USE_DATASTORE - User is not Server Admin or above and requested to force the datastore type. (See DBCREATE_xxx(2).)
ERR_DB2NSF_NOT_ENABLED_FOR_DB2 - Server is not DB2-enabled and Option2 = DBCREATE_FORCE_DB2_DATASTORE.
ERR_xxx - Errors returned by lower level functions.   Use OSLoadString to display/log a description of the error.



**See Also :**
[DBCLASS_xxx](/reference/Symb/DBCLASS_xxx)
[DBCREATE_ENCRYPT_xxx](/reference/Symb/DBCREATE_ENCRYPT_xxx)
[DBCREATE_xxx](/reference/Symb/DBCREATE_xxx)
[DBCREATE_xxx(2)](/reference/Symb/DBCREATE_xxx(2))
[NSFDbCreate](/reference/Func/NSFDbCreate)
[NSFDbOpen](/reference/Func/NSFDbOpen)
[OSPathNetConstruct](/reference/Func/OSPathNetConstruct)
---
