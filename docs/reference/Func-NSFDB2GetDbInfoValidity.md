##### Function : Backup
##### NSFDB2GetDbInfoValidity - Validate NSFDB2 database information.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDB2GetDbInfoValidity(**

	const char *filePath,
	char *Schema,
	DWORD  szSchema,
	char *tableSpace,
	DWORD  szTableSpace,
	char *actualTableSpace,
	DWORD  szActualTableSpace,
	BOOL *schemaExists,
	BOOL *tsExists,
	BOOL *tsMismatch,
	DWORD  flags);
**Description :**
This function returns the schema  and table space that Domino believes the 
specified NSFDB2 database exists in.  It also returns a status of whether or 
not the schema and table space exists.  
**Parameters :**
Input :
filePath  -  The file name of the NSFDB2 database.

szSchema  -  The size of the buffer allocated for Schema.

szTableSpace  -  The size of the buffer allocated for tableSpace.

szActualTableSpace  -  The size of the buffer allocated for actualTableSpace.

flags  -  (Reserved for future use.)  Must be 0.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successful.

ERR_DB2NSF_CLI_ERROR - Internal DB2/CLI error.

ERR_NOT_FOUND - NSFDB2 information could not be found for filePath

ERR_DB2NSF_NOT_ENABLED_FOR_DB2 - The Domino server is not enabled for DB2.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


Schema  -  The name of the DB2 schema containing the tables for the NSFDB2 db.

tableSpace  -  The name of the table space as recorded in Domino's CATALOG table.

actualTableSpace  -  The real container location (table space) of Schema.NSFNOTE

schemaExists  -  True if the Schema specified in Domino's CATALOG table exists.

tsExists  -  True if the table space referenced in Domino's CATALOG table exists.

tsMismatch  -  True if the table space actually containing Schema.NSFNOTE differs from what Domino's CATALOG table has listed for filePath.  This will only happen with DBA intervention or through backup/restore scenarios (e.g. renaming a table space from the DB2 Control Center application)

**See Also :**
[NSFDB2GetInfo](D:/md_files/NSFDB2GetInfo.md)
[NSFDB2GetServerInfo](D:/md_files/NSFDB2GetServerInfo.md)
[NSFDB2ListNSFDB2Databases](D:/md_files/NSFDB2ListNSFDB2Databases.md)
[NSFDB2ReconnectNotesDatabase](D:/md_files/NSFDB2ReconnectNotesDatabase.md)
---
