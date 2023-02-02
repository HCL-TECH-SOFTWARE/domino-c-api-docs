##### Function : Database
##### NSFDbMajorMinorVersionGet - Get the major and minor version numbers for an open database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbMajorMinorVersionGet(**

	DBHANDLE  hDB,
	WORD far *retMajorVersion,
	WORD far *retMinorVersion);
**Description :**
The NSFDbMajorMinorVersionGet API routine allows a C API program to obtain the 
major and minor version numbers of an open database.  The major version number 
indicates which releases of Domino and Notes software are able to access that 
database.  The major verson number of a database is the same as the ODS version 
number that is displayed in the Notes Client File/Database/Properties/second 
information tab.  The minor version number indicates small changes to the 
internal format of a database, and is generally of little interest to a C API 
program.  Each release of Domino or Notes software can access databases that 
have a major version number that is less than or equal to a particular value 
associated with that release.  A Domino database that has a major version 
number that is greater than the major version number associated with a 
particular Domino or Notes release cannot be accessed by that release.  The 
following table shows which major version numbers can be accessed by particular 
releases of Domino or Notes:


Domino or Notes Software Releases	Major Version Numbers That Can Be Accessed
1.x	16
2.x	16
3.x	17 or less
4.0, 4.1, 4.5x, 4.6.x
5.0 - 5.0.12, 6 - 6.0.3, 6.5, 7.0
9.0	20 or less
	43 or less
	52

**Parameters :**
Input :
hDB  -  A handle to a Domino database.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully got major and minor version numbers for this database.

ERR_FUNC_NOT_IMPL -  The requested function is not supported by the software on this server.


retMajorVersion  -  The address of a WORD into which the major version number of the database is returned.

retMinorVersion  -  The address of a WORD into which the minor version number of the database is returned.

**Sample Usage :**
```
/* Output major and minor version numbers */
 
if (rc = NSFDbMajorMinorVersionGet(db_handle, &major_ver, &minor_ver))
      goto Exit;

printf("\nMajor ver: %d, minor ver: %d\n", major_ver, minor_ver);
```
**See Also :**
[NSFDbClose](D:/md_files/NSFDbClose.md)
[NSFDbGetBuildVersion](D:/md_files/NSFDbGetBuildVersion.md)
[NSFDbOpen](D:/md_files/NSFDbOpen.md)
[NSFDbOpenExtended](D:/md_files/NSFDbOpenExtended.md)
---
