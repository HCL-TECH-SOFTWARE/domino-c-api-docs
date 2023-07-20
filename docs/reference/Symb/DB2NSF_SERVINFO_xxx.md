##### Symbolic Value : Database
##### DB2NSF_SERVINFO_xxx - Flag for NSFDB2GetServerInfo.
---
```
#include <nsfdb.h>
```

**Symbolic Values :**

	DB2NSF_SERVINFO_SERVER_DEFAULT_TYPE	  -  Either of the NULL terminated strings: "DB2" or "NSF", in LIMBCS.

	DB2NSF_SERVINFO_NSFDB2_CAPABLE	  -  Determine if Domino capable of serving NSFDB2 data. If the server can host NSFDB data, the buffer will contain a "1". If the server is not properly set up to host NSFDB2 data, the buffer will contain a "0". Maximum returned buffer size for this flag is "sizeof(DWORD)".

	DB2NSF_SERVINFO_DB2_DATABASE_NAME	  -  DB2 database name.


**Description :**

The type of information for NSFDB2GetServerInfo to return.


**See Also :**
[NSFDB2GetServerInfo](/domino-c-api-docs/reference/Func/NSFDB2GetServerInfo)
---
