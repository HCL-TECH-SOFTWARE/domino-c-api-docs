##### Function : Events
##### EventQueueGet - Remove an event from an event queue.
---
```
#include <event.h>
STATUS LNPUBLIC EventQueueGet(

	char far *QueueName,
	DHANDLE far *rethEvent);
```
**Description :**

Remove an event from an event queue, and return a pointer to the handle of the 
EVENT_DATA structure associated with the event.  See the definition of 
EVENT_DATA for more information.

**Parameters :**
Input :
QueueName  -  A far pointer to the name of the queue in which to look for events.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - An event was found in the queue.
ERR_EVTQUEUE_EMPTY - There were no events in the queue.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


rethEvent  -  A pointer to a handle to the EVENT_DATA structure associated with the event.  


**See Also :**
[EventDeregisterEventRequest](/domino-c-api-docs/reference/Func/EventDeregisterEventRequest)
[EventGetDestName](/domino-c-api-docs/reference/Func/EventGetDestName)
[EventQueueAlloc](/domino-c-api-docs/reference/Func/EventQueueAlloc)
[EventQueueFree](/domino-c-api-docs/reference/Func/EventQueueFree)
[EventQueuePut](/domino-c-api-docs/reference/Func/EventQueuePut)
[EventRegisterEventRequest](/domino-c-api-docs/reference/Func/EventRegisterEventRequest)
---
