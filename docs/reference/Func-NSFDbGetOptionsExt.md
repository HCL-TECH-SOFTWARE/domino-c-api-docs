##### Function : Database
##### NSFDbGetOptionsExt - Get DB option flags from a database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbGetOptionsExt(**

	DBHANDLE  hDB,
	DBOPTIONS  retDbOptions);
**Description :**
Get the option flags that are set for a given database. The option flags are 
described in the entry DBOPTION_xxx. Refer to DBOPTION_xxx for more 
information. 

If the database is on a remote server and not cached locally, return the 
database option flags from the server. If the database is cached locally, 
return the DBOPTION_xxx from the local cache.

If the database is local, return the database option flags from the database. 

Note - more DBOPTION_xxx values will be published in the future.
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
[](D:/md_files/.md)
---
