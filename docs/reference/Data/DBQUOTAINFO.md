##### Data Type : Database
##### DBQUOTAINFO - Database quota structure.
---
```
#include <nsfdata.h>
```

**Definition :**

typedef struct {
   DWORD WarningThreshold; /* Database size warning threshold
                              (in kbyte units) */
   DWORD SizeLimit;        /* Database size limit
                              (in kbyte units) */
   DWORD CurrentDbSize;     /* Current size of database
                              (in kbyte units) */
   DWORD MaxDbSize;        /* Max database file size possible
                              (in kbyte units) */
} DBQUOTAINFO;

**Description :**

This structure is used by NSFDbQuotaSetExt() and returned by NSFDbQuotaGet().  It contains the database quota information.


**See Also :**
[DBQUOTAINFOEXT](/domino-c-api-docs/reference/Data/DBQUOTAINFOEXT)
[DBQUOTA_xxx](/domino-c-api-docs/reference/Symb/DBQUOTA_xxx)
[NSFDbQuotaGet](/domino-c-api-docs/reference/Func/NSFDbQuotaGet)
[NSFDbQuotaSetExt](/domino-c-api-docs/reference/Func/NSFDbQuotaSetExt)
---
