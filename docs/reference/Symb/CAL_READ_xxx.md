##### Symbolic Value : iCalendar
##### CAL_READ_xxx - Flags that control behavior of the calendar APIs that return iCalendar data for an entry or notice
---
```
#include <calapi.h>
```

**Symbolic Values :**

	CAL_READ_HIDE_X_LOTUS	  -  By default, some X-LOTUS properties and parameters will be included in iCalendar data returned by these APIs. CAL_READ_HIDE_X_LOTUS causes all X-LOTUS properties and parameters to be removed from the generated iCalendar data.
Note: This overrides CAL_READ_INCLUDE_X_LOTUS

	CAL_READ_INCLUDE_X_LOTUS	  -  Include all Lotus specific properties like X-LOTUS-UPDATE-SEQ, X-LOTUS-UPDATE_WISL, etc in the generated iCalendar data.These properties are NOT included by default in any iCalendar data returned by the APIs.
Caution: Unless the caller knows how to use these it can be dangerous since their presence will be honored and can cause issues if not updated properly.
Ignored if CAL_READ_HIDE_X_LOTUS is also specified.


**Description :**




**See Also :**
---
