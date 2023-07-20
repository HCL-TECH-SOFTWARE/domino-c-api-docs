##### Data Type : Database
##### BUILDVERSION - Build information structure
---
```
#include <nsfdb.h>
```

**Definition :**
```
typedef struct {
	DWORD MajorVersion; /* Major version identifier */
	DWORD MinorVersion; /* Minor version identifier */
	DWORD QMRNumber;  /* Maintenance Release identifier */
	DWORD QMUNumber;  /* Maintenance Update identifier */
	DWORD HotfixNumber; /* Hotfixes installed on machine */ 
	DWORD Flags;  /* See BUILDVERFLAGS_xxx */
	DWORD FixpackNumber; /* Fixpack version installed on machine */
	DWORD Spare[2];  /* Room for growth */
	} BUILDVERSION;
```

**Description :**

Structure returned by NSFDbGetMajMinVersion to determine code level at runtime


**See Also :**
[BLDVERFLAGS_xxx](/domino-c-api-docs/reference/Symb/BLDVERFLAGS_xxx)
[NSFDbGetMajMinVersion](/domino-c-api-docs/reference/Func/NSFDbGetMajMinVersion)
---
