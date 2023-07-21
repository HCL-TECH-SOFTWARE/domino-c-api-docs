##### Symbolic Value : Database
##### DB_xxx (NSFDbModeGet) - Specifies whether a DBHANDLE is associated with a database or with a directory.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DB_LOADED	  -  The DBHANDLE is a handle to a database.

	DB_DIRECTORY	  -  The DBHANDLE is a handle to a directory.


**Description :**

The function NSFDbModeGet returns one of these values to indicate whether a DBHANDLE is a handle to a database or a handle to a directory.


**See Also :**
[NSFDbModeGet](/domino-c-api-docs/reference/Func/NSFDbModeGet)
[NSFDbOpen](/domino-c-api-docs/reference/Func/NSFDbOpen)
---
