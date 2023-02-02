##### Function : Database
##### NSFDbGetOptions - Retrieve database option flags.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbGetOptions(**

	DBHANDLE  hDB,
	DWORD far *retDbOptions);
**Description :**
Get the option flags set for this database.  The option flags are described in 
the entry DBOPTION_xxx.
**Parameters :**
Input :
hDB  -  Handle of the database.

Output :
(routine)  -  Return status from this call -- indicates either success, or what the error is.  The return codes include:

NOERROR - Successfully retrieved database option flags.

ERR_SPECIAL_ID - No database option flags were found in this database.  This means that no database option flags were set for this database.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



retDbOptions  -  Option flags for this database are stored at this address.

**See Also :**
[NSFDbSetOptions](D:/md_files/NSFDbSetOptions.md)
[DBOPTION_xxx](D:/md_files/DBOPTION_xxx.md)
---
