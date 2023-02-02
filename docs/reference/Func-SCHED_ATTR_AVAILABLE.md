##### Function : Calendaring and Scheduling
##### SCHED_ATTR_AVAILABLE - Check if time is available.
---
##### #include <nsfdata.h>
BOOL **SCHED_ATTR_AVAILABLE(**

	BYTE  attr);
**Description :**
Implemented as a macro:

#define SCHED_ATTR_AVAILABLE(attr) (!((attr) & SCHED_ATTR_BUSY_BASE))
**Parameters :**
Input :
attr  -  The attributes for this schedule entry.

Output :
(routine)  -  Returns TRUE if it is an available time, FALSE if it is a busy time.


**See Also :**
[SCHED_ENTRY](D:/md_files/SCHED_ENTRY.md)
---
