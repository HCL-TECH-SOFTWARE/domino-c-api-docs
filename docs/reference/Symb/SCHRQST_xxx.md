##### Symbolic Value : Calendaring and Scheduling
##### SCHRQST_xxx - Option flags for scheduling.
---
```
#include <schedule.h>
```

**Symbolic Values :**

	SCHRQST_COMPOSITE	  -  Return composite schedule.

	SCHRQST_EACHPERSON	  -  Return each person's schedule.

	SCHRQST_LOCAL	  -  Do only local lookup.

	SCHRQST_FORCEREMOTE	  -  Force remote lookups even if workstation based mail.

	SCHRQST_EXTFORMAT	  -  Get busytime in the SCHED_ENTRY_EXT format instead of the pre-Domino 6 SCHED_ENTRY format . Note that this flag does not guarantee that data will be in SCHED_ENTRY_EXT format. Pre-Domino 6 busytime data will remain in SCHED_ENTRY format. To determine which format is used, check the Spare member of the SCHED_LIST structure. If 0, the data is in SCHED_ENTRY format, otherwise the data is in SCHED_ENTRY_EXT format.


**Description :**

Option flags used in scheduling API calls such as SchRetrieve.


**See Also :**
[SCHED_LIST](/domino-c-api-docs/reference/Data/SCHED_LIST)
[SchRetrieve](/domino-c-api-docs/reference/Func/SchRetrieve)
[SchSrvRetrieve](/domino-c-api-docs/reference/Func/SchSrvRetrieve)
[SchSrvRetrieveExt](/domino-c-api-docs/reference/Func/SchSrvRetrieveExt)
---
