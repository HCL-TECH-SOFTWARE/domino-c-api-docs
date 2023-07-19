##### Symbolic Value : Events
##### SEV_xxx - Describes the severity of a user-generated event.
---
```
#include <event.h>
```

**Symbolic Values :**

	SEV_UNKNOWN	  -  The severity of the event is unknown

	SEV_FATAL	  -  This event indicates a fatal condition.

	SEV_FAILURE	  -  This event indicates a failure of some sort.

	SEV_WARNING1	  -  This event serves as a warning (High priority).

	SEV_WARNING2	  -  This event serves as a warning (Low priority).

	SEV_NORMAL	  -  This event signifies that processing is continuing normally.


**Description :**

These are the permissible values for the &quot;Severity&quot; member of the EVENT_DATA data structure. 


**See Also :**
[EVENT_DATA](/domino-c-api-docs/reference/Data/EVENT_DATA)
[EVT_xxx](/domino-c-api-docs/reference/Symb/EVT_xxx)
---
