##### Symbolic Value : Database
##### DB2NSF_INFO_xxx - Flags for NSFDB2GetInfo.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DB2NSF_INFO_IS_DB2_BACKED	  -  If the database is DB2, the buffer will contain a "1". If the database is NSF, the buffer will contain a "0". Maximum returned buffer size for this flag is "sizeof(DWORD)".

	DB2NSF_INFO_SCHEMA_NAME	  -  The name, in LMBCS, of the database schema.

	DB2NSF_INFO_TABLESPACE_NAME	  -  The name, in LMBCS, of the DB2 tablespace.

	DB2NSF_INFO_TSID	  -  (LUW only) returns TSID of DB2 tablespace containing NSFDB2 database

	DB2NSF_INFO_USERSCHEMA_NAME	  -  returns the user schema associated with Domino Access View table & view data.

	DB2NSF_INFO_CLASS_DESC	  -  The nsfdb2 class designation that can be used by third party software applications to group similar NSFDB2 databases.


**Description :**

The type of information for NSFDB2GetInfo to return.


**See Also :**
[NSFDB2GetInfo](/domino-c-api-docs/reference/Func/NSFDB2GetInfo)
---
