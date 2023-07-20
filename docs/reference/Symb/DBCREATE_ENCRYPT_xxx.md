##### Symbolic Value : Database
##### DBCREATE_ENCRYPT_xxx - NSFDbCreateExtended - EncryptStrength
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DBCREATE_ENCRYPT_NONE	  -  Do not locally encrypt database.

	DBCREATE_ENCRYPT_SIMPLE	  -  Locally encrypt this database with simple level encryption.

	DBCREATE_ENCRYPT_MEDIUM	  -  Locally encrypt this database with medium level encryption.

	DBCREATE_ENCRYPT_STRONG	  -  Locally encrypt this database with strong level encryption.


**Description :**

Local encryption level for this database.  A locally encrypted database cannot be opened locally without the appropriate user ID.  Refer to the Notes Help documentation for a detailed description of the various local encryption levels.


**See Also :**
[NSFDbCreateExtended](/domino-c-api-docs/reference/Func/NSFDbCreateExtended)
---
