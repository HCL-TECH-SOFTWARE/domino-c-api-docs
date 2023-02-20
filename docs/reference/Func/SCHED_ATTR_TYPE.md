##### Function : Calendaring and Scheduling
##### SCHED_ATTR_TYPE - Check schedule attributes.
---
```
#include <nsfdata.h>
BYTE SCHED_ATTR_TYPE(

	BYTE  attr);
```
**Description :**

Implemented as a macro:

#define SCHED_ATTR_TYPE(attr) ((attr) & SCHED_ATTR_TYPE_BITS)

**Parameters :**
Input :
attr  -  The attributes you want to check.

Output :
(routine)  -  Returns the set attributes.



**See Also :**
[SCHED_ENTRY](/reference/Data/SCHED_ENTRY)
---
