##### Data Type : Database
##### DBQUOTAINFOEXT - Extended database quota structure.
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
   DWORD WarningThreshold; /* Database size warning threshold in kbyte units */
   DWORD SizeLimit;  /* Database size limit in kbyte units */
   DWORD CurrentDbSize; /* Current size of database (in kbyte units) */
   DWORD MaxDbSize;  /* Max database file size possible (in kbyte units) */
   WORD QuotaMethod;  /* Enforcement method - filesize or usage */
   DWORD CurrentUsage; /* Current amount of space used in the database (in 
kbyte units) */
   DWORD CurrentSizeUsed; /* Either CurrentDbSize, or CurrentUsage, depending 
on method in use */
   DWORD Unused1;  /* Reserved.  Unused */
   DWORD Unused2;  /* Reserved.  Unused */
} DBQUOTAINFOEXT;
```

**Description :**

This structure is returned by NSFDbQuotaGethDB().  It contains the database quota information and quota method.


**See Also :**
[DBQUOTAINFO](/domino-c-api-docs/reference/Data/DBQUOTAINFO)
[NSF_QUOTA_METHOD_xxx](/domino-c-api-docs/reference/Symb/NSF_QUOTA_METHOD_xxx)
---
