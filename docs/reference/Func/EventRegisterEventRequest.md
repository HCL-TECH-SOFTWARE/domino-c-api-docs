##### Function : Events
##### EventRegisterEventRequest - Specify the type and severity of events an event consumer will process.
---
```
#include <event.h>
STATUS LNPUBLIC EventRegisterEventRequest(

	WORD  EventType,
	WORD  EventSeverity,
	char far *QueueName,
	char far *DestName);
```
**Description :**

This function is called by an event consumer to specify to the Domino Event 
Handler that the consumer wishes to process events of a certain type and 
severity.  The consumer must call EventRegisterEventRequest once for each 
combination of event type and severity in which it is interested.

**Parameters :**
Input :
EventType  -  The type of event in which the event consumer is interested.  See the definition of EVT_xxx for permissible values.

EventSeverity  -  The severity of events in which the event consumer is interested.  See the definition of SEV_xxx for permissible values.

QueueName  -  A pointer to the name of the queue that will receive events.

DestName  -  A string containing the name of a person or database to be associated with events of this type and severity.  When an event of this type and severity is consumed, the consumer may retrieve this name by calling the function EventGetDestName.  If the consumer desires it  may then record the event occurrence by either notify the person named,  or by writing to the database named, whichever is appropriate.


Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.





**See Also :**
[EventQueueAlloc](/reference/Func/EventQueueAlloc)
[EventQueueFree](/reference/Func/EventQueueFree)
[EventQueuePut](/reference/Func/EventQueuePut)
[EventQueueGet](/reference/Func/EventQueueGet)
[EventDeregisterEventRequest](/reference/Func/EventDeregisterEventRequest)
[EventGetDestName](/reference/Func/EventGetDestName)
---
