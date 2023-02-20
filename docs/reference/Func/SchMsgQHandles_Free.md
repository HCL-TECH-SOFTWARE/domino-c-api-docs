##### Function : Calendaring and Scheduling
##### SchMsgQHandles_Free - Close the schedule gateway message queues.
---
```
#include <schgtw.h>
void LNPUBLIC SchMsgQHandles_Free(

	MQHANDLE  hInputQ,
	MQHANDLE  hOutputQ);
```
**Description :**

This routine closes the schedule gateway message queues.

**Parameters :**
Input :
hInputQ  -  Handle to an open input queue

hOutputQ  -  Handle to an open output queue



**See Also :**
[SchMsgQHandles_New](/reference/Func/SchMsgQHandles_New)
---
