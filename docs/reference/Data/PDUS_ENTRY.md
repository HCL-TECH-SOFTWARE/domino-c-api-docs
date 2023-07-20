##### Data Type : Domino Upgrade Services
##### PDUS_ENTRY - Pointer to DUS (Domino Upgrade Service) user/group entry available for migration.
---
```
#include <dus.h>
```

**Definition :**
```
typedef struct
{
char Name[DUSMAXFLATNAME+1]; /* required -- user or group name */
DWORD ID;      /* required -- unique value identifying this user or group */
DWORD EntryFlags;    /* not to be used by the DUS */
DHANDLE hParentGroupList;  /*  Optional and rarely used.  Alloced by the DUS or 
Notes and freed by Notes.
	        Contains a Notes LIST of group names to which the entry belongs.
	        This can be adjusted by Notes after DUSInitialize, depending
	        on administrator choices at the UI, but can be initially set
	        by the DUS.  This LIST handle must be created with the
	        prefix data type set to FALSE (see ListAllocate) and must
	        be passed UNLOCKED back to Notes. */
} *PDUS_ENTRY;

```

**Description :**




**See Also :**
[DUS_ENTRY](/domino-c-api-docs/reference/Data/DUS_ENTRY)
---
