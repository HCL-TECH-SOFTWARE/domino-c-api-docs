##### Function : Events
##### EventDeregisterEventRequest - Discontinue notification of particular events.
---
```
#include <event.h>
STATUS LNPUBLIC EventDeregisterEventRequest(

	WORD  EventType,
	WORD  EventSeverity,
	char far *QueueName);
```
**Description :**

This function is called by an event consumer to specify to the Domino Event 
Handler that the consumer is no longer interested in processing events of a 
certain type and severity.

**Parameters :**
Input :
EventType  -  The type of event in which the event consumer is no longer interested.  See the definition of EVT_xxx for permissible values.

EventSeverity  -  The severity of events in which the event consumer is no longer interested.  See the definition of SEV_xxx for permissible values.

QueueName  -  A pointer to the name of the queue that receives events that are no longer desired..

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.





**See Also :**
[EventQueueAlloc](/reference/Func/EventQueueAlloc)
[EventQueueFree](/reference/Func/EventQueueFree)
[EventQueuePut](/reference/Func/EventQueuePut)
[EventQueueGet](/reference/Func/EventQueueGet)
[EventRegisterEventRequest](/reference/Func/EventRegisterEventRequest)
[EventGetDestName](/reference/Func/EventGetDestName)
---
