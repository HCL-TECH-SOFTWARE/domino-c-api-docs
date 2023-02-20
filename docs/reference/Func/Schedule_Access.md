##### Function : Calendaring and Scheduling
##### Schedule_Access - Get access to a schedule object.
---
```
#include <schedule.h>
STATUS LNPUBLIC Schedule_Access(

	HCNTNR  hCntnr,
	HSCHEDULE  hSched,
	SCHEDULE FAR **pretSched);
```
**Description :**

This function returns a pointer to a schedule object.

**Parameters :**
Input :
hCntnr  -  A handle to the schedule container.

hSched  -  A handle to the existing schedule.

Output :
(routine)  -  NOERROR - Successfully returned access to a SCHEDULE object.
ERR_xxx (See ERR_xxx for possible values).


pretSched  -  Returns a pointer to a SCHEDULE structure.


**See Also :**
---
