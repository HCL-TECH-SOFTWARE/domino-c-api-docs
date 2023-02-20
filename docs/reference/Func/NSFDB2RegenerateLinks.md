##### Function : Backup
##### NSFDB2RegenerateLinks - Verify that all link files exist on the Domino server's data directory.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDB2RegenerateLinks(

	DWORD  flags);
```
**Description :**

This function can be used after a DB2 database restore to make sure that all 
link files exist on the Domino server's data directory.   This function can 
also be used if a Domino server's data directory was erased and restored from a 
NSF-specific backup in order to regenerate the link files for all DB2 Domino 
data.    This function can also be used to verify that links to NSFDB2 
databases are valid.

Notes:
This function can only be run on the Domino server when the server is down.
Actions taken by this API call will be logged.

**Parameters :**
Input :
flags  -  See DB2BACKUP_LINKS_xxx.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successful.

ERR_DB2BACKUP_SERVERRUNNING - The Domino server cannot be running when this command executes.

ERR_DB2NSF_CLI_ERROR - Internal DB2/CLI error.

ERR_DB2NSF_NOT_ENABLED_FOR_DB2 - The Domino server is not enabled for DB2.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**See Also :**
[DB2BACKUP_LINKS_xxx](/reference/Symb/DB2BACKUP_LINKS_xxx)
[NSFDB2GetInfo](/reference/Func/NSFDB2GetInfo)
[NSFDB2GetServerInfo](/reference/Func/NSFDB2GetServerInfo)
[NSFDB2ListNSFDB2Databases](/reference/Func/NSFDB2ListNSFDB2Databases)
[NSFDB2ReconnectNotesDatabase](/reference/Func/NSFDB2ReconnectNotesDatabase)
---
