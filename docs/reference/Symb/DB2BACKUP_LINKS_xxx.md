##### Symbolic Value : Backup
##### DB2BACKUP_LINKS_xxx - NSFDB2 regenerate links flags.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DB2BACKUP_LINKS_VERIFYEXISTING	  -  Validate existing NSFDB2 database link files in the Domino server's data directory and subdirectories to make sure the link files point to valid NSFDB2 databases.

	DB2BACKUP_LINKS_SCANSCHEMAS	  -  Scan all schemas defined in the DB2 database to determine what rows may be missing from the Domino server's CATALOG table.

	DB2BACKUP_LINKS_QUIET	  -  Use this flag if you do not wish NSFDB2RegenerateLinks to log its activity.


**Description :**

These values are for the flags parameter of NSFDB2RegenerateLinks.


**See Also :**
[NSFDB2RegenerateLinks](/domino-c-api-docs/reference/Func/NSFDB2RegenerateLinks)
---
