##### Symbolic Value : Database
##### DBCREATE_xxx(2) - NSFDbCreateExtendedWithOptions - Options
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DBCREATE_USE_SERVER_DEFAULT_DATASTORE	  -  Use server default database type.

	DBCREATE_FORCE_NSF_DATASTORE	  -  Use NSF database type (must have proper authorization.)

	DBCREATE_FORCE_DB2_DATASTORE	  -  Use DB2 database type (must have proper authorization.)

	DBCREATE_UNDEFINED_OPTIONS2	  -  DBCREATE_USE_SERVER_DEFAULT_DATASTORE | DBCREATE_FORCE_NSF_DATASTORE | 						DBCREATE_FORCE_DB2_DATASTORE | DBCREATE_OVERRIDE_ADMINP


**Description :**

Database creation options.


**See Also :**
[NSFDbCreateExtendedWithOptions](/domino-c-api-docs/reference/Func/NSFDbCreateExtendedWithOptions)
---
