##### Symbolic Value : User Registration
##### REG_ROAMING_CLEANUP_xxx - Roaming cleanup values.
---
```
#include <reg.h>
```

**Symbolic Values :**

	REG_ROAMING_CLEANUP_NEVER	  -  Roaming client will not cleanup.

	REG_ROAMING_CLEANUP_EVERY_NDAYS	  -  Roaming client will cleanup every N days.

	REG_ROAMING_CLEANUP_AT_SHUTDOWN	  -  Roaming client will cleanup at shutdown.

	REG_ROAMING_CLEANUP_PROMPT	  -  Roaming client will prompt for cleanup.


**Description :**

Roaming cleanup values for the CleanupSetting member of the REG_ROAMING_INFO structure.


**See Also :**
[REG_ROAMING_INFO](/domino-c-api-docs/reference/Data/REG_ROAMING_INFO)
---
