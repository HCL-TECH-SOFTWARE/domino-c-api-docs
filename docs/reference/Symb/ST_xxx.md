##### Symbolic Value : Statistics Reporting
##### ST_xxx - Flags for StatUpdate.
---
```
#include <stats.h>
```

**Symbolic Values :**

	ST_UNIQUE	  -  Statistic is unique - only one instance is allowed.

	ST_ADDITIVE	  -  Value type of statistic is VT_LONG or VT_NUMBER and the new value is to be added to the current value of the statistic.

	ST_RESETABLE	  -  Statistic is resetable to 0.


**Description :**

These are the values you may specify in the Flags parameter to StatUpdate(). Specify a Flags value of 0 to prevent StatUpdate from taking any of these actions.


**See Also :**
[StatUpdate](/domino-c-api-docs/reference/Func/StatUpdate)
---
