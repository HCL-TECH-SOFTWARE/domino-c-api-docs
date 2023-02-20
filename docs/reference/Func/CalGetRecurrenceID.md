##### Function : iCalendar
##### CalGetRecurrenceID - This is a convinience method that returns a RECURRENCE-ID (in UTC time) from a TIMEDATE object.
---
```
#include <calapi.h>
STATUS CalGetRecurrenceID(

	TIMEDATE  tdInput,
	char*pszRecurID,
	WORD  wLenRecurId);
```
**Description :**



**Parameters :**
Input :
tdInput  -  Input time/date object.

wLenRecurId  -  Buffer to populate with the reuccence-ID representation.

Output :
(routine)  -  NOERROR on success
ERR_MISC_INVALID_ARGS		Unexpected arguments provided
ERR_VALUE_LENGTH			The value is too long for the allocated buffer


pszRecurID  -  Buffer to populate with the reuccence-ID representation.


**See Also :**
---
