##### Symbolic Value : Agents
##### ASSISTINTERVAL_TYPE_xxx - ODS_ASSISTSTRUCT - wIntervalType values for agent interval types.
---
```
#include <queryods.h>
```

**Symbolic Values :**

	ASSISTINTERVAL_TYPE_NONE	  -  No interval type specified.

	ASSISTINTERVAL_TYPE_MINUTES	  -  The wInterval field contains the interval between invocations in minutes. dwTime1 contains the local time of the day when the Agent should start execution, and dwTime2 contains the local time of day after which the Agent should not be executed. dwTime1 and dwTime2 are specified in 10-millisecond "ticks" since local midnight.

	ASSISTINTERVAL_TYPE_DAYS	  -  The wInterval field contains the interval between invocations in days. dwTime1 contains the local time of the day when the Agent should be run, specified in 10-millisecond "ticks" since local midnight. dwTime2 is not used.

	ASSISTINTERVAL_TYPE_WEEK	  -  The wInterval field contains the interval between invocations in weeks. dwTime1 contains the local time of the day when the Agent should be run, specified in 10-millisecond "ticks" since local midnight. dwTime2 contains an integer from 0 to 6 specifying the day of the week when the Agent should be run.

	ASSISTINTERVAL_TYPE_MONTH	  -  The wInterval field contains the interval between invocations in months. dwTime1 contains the local time of the day when the Agent should be run, specified in 10-millisecond "ticks" since local midnight. dwTime2 contains an integer from 0 to 31 specifying the day of the month when the Agent should be run.

	ASSISTINTERVAL_TYPE_EVENT	  -  The wInterval field contains the interval between invocations of eventss. dwTime1 contains the local time of the day when the Agent should be run, specified in 10-millisecond "ticks" since local midnight. dwTime2 is not used.


**Description :**

The interval type codes are stored in the wIntervalType field of the ODS_ASSISTSTRUCT for an Agent.  The interval type code determines the intrepretation of the wInterval, dwTime1, and dwTime2 fields in the structure.


**See Also :**
[ODS_ASSISTSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTSTRUCT)
---
