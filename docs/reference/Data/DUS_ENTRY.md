##### Data Type : Domino Upgrade Services
##### DUS_ENTRY - Represents one user or group being imported via a DUS process.
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
} DUS_ENTRY;

```

**Description :**

An array of these structures is allocated by Domino and passed in to the DUS with DUSRetrieveUsers and DUSRetrieveGroups. The DUS fills in the data and the DUS_ENTRY is passed back to Domino, where the data is displayed in the &quot;Foreign Directory Import&quot; dialog box within the list of &quot;Available users/groups&quot; under registration for a user.  You are responsible for allocating memory for each DUS_ENTRY with OSMemAlloc() and freeing the memory with OSMemFree().


**See Also :**
[DUSRetrieveGroups](/domino-c-api-docs/reference/Func/DUSRetrieveGroups)
[DUSRetrieveUsers](/domino-c-api-docs/reference/Func/DUSRetrieveUsers)
---
