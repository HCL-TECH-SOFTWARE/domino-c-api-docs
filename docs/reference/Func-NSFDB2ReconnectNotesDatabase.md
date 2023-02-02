##### Function : Backup
##### NSFDB2ReconnectNotesDatabase - Make sure that Domino can access NSFDB2 data for FullPath or rename the NSFDB2 database within the Domino server 
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDB2ReconnectNotesDatabase(**

	const char far *FullPath,
	const char far *String1,
	DWORD  nsfid,
	DWORD  flags);
**Description :**
A utility function to make sure the infrastructure is in place such that Domino 
can access NSFDB2 data for FullPath.   This can also be used to effectively 
rename the NSFDB2 database within the Domino server by assigning a new FullPath 
if nsfid is provided.

String1 defines a logical grouping of NSFDB2 databases.  For DB2 UDB on LUW, 
the groupName  should be synonymous with DB2 tablespace name.   If FullPath is 
NULL or an empty string, and DB2BACKUP_NONSFID is passed as nsfid, all NSFDB2 
databases specified by String1 will be reconnected.  This will be useful for 
UDB 9.1 where a missing tablespace could be restored to the current DB2 
database or another DB2 database.

This function will only affect the current server's data directory.  It can not 
be executed on a remote server.

Algorithm :
If FullPath  or nsfid  is provided, scan all properties tables in the 
tablespace specified by string1, until we find one in a schema that claims to 
containing data for FullPath. or nsfid
Iff one row is found:
Extract the NSFID from the properties table found in the above step.
Update Domino's CATALOG table.
Make sure link file on  Domino server's file system exists.
If DB2BACKUP_FASTCONNECT is not specified as an option, restore function and 
trigger definitions for access tables & views, removing old values if necessary.
If DB2BACKUP_NOREPLICA is specified in flags, regenerate the REPLICA ID of this 
database.
Else return ERR_DB2NSF_IDENTIFIER_INVALID.
If FullPath and nsfid was not provided
Reconnect NSFDB2 databases discovered in the DB2 tablespace by scanning 
PROPERTIES table in groupName for NSFDB2 data and verifying the data actually 
exists.  Reconnect the NSFDB2 database as described above.

**Parameters :**
Input :
FullPath  -  Relative to the Domino server's data directory.  This does not have to be the same as the original path.

String1  -  NSFDB2 group (DB2 tablespace) containing the NSFDB2 database you wish to reconnect.


nsfid  -  (optional) Normally pass DB2BACKUP_NONSFID so parameter is ignored.  Otherwise, Domino unique internal identifier for FullPath..

flags  -  optional.  
          See DB2BACKUP_xxx.

Output :
(routine)  -  STATUS, including the following:
NOERROR
ERR_DB2NSF_CLI_ERROR - Internal DB2/CLI error.
ERR_DB2NSF_NOT_ENABLED_FOR_DB2 - The Domino server is not enabled for DB2.
ERR_DB2NSF_IDENTIFIER_INVALID  - If the tablespace (or schema for iSeries) specified is invalid or doesn't contain data for the NSFDB2 database specified by FullPath
ERR_EXISTS - The file specified by FullPath already exists and is not a link file for a NSFDB2 database, or it exists in another DB2 tablespace or schema.


**See Also :**
[DB2BACKUP_xxx](D:/md_files/DB2BACKUP_xxx.md)
[NSFDB2GetInfo](D:/md_files/NSFDB2GetInfo.md)
[NSFDB2GetServerInfo](D:/md_files/NSFDB2GetServerInfo.md)
[NSFDB2ListNSFDB2Databases](D:/md_files/NSFDB2ListNSFDB2Databases.md)
[NSFDB2RegenerateLinks](D:/md_files/NSFDB2RegenerateLinks.md)
---
