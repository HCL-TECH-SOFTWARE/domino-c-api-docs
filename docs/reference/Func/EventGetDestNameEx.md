##### Function : Events
##### EventGetDestNameEx - Retrieve the user or database name associated with an event.
---
```
#include <event.h>
BOOL LNPUBLIC EventGetDestNameEx(

	WORD  EventType,
	WORD  EventSeverity,
	char *ErrorCode,
	char *ErrorText,
	char *QueueName,
	char *DestName,
	WORD  DestNameSize);
```
**Description :**

When an event is registered, the event consumer may specify the name of a user 
or a database that is to be associated with events of this particular type, 
severity, code and text.  When a consumer has consumed an event, it can call 
EventGetDestNameEx to retrieve the name.  The consumer can then take whatever 
appropriate action is required - it may log a message to the database named, 
for example.

**Parameters :**
Input :
EventType  -  The type of event in which the event consumer is interested.  See the definition of EVT_xxx for permissible values.

EventSeverity  -  The severity of the event in which the event consumer is interested.  See the definition of SEV_xxx for permissible values.

ErrorCode  -  Pointer to the error code associated with the given event (see EVENT_DATA.)

ErrorText  -  Pointer to the event specific data associated with the given event (see EVENT_DATA.)

QueueName  -  A pointer to the name of the queue receiving the events.

DestNameSize  -  Size of the buffer to receive the destination name.

Output :
(routine)  -  Return status from this call -- indicates either success or failure.


DestName  -  A string containing the name of a person or database to be associated with events of this type and severity.  When an event of this type and severity is consumed, the consumer may retrieve this name by calling the function EventGetDestNameEx.  If desired, the consumer   may then record the event occurrence by either notifying the person named,  or by writing to the database named, whichever is appropriate.


**See Also :**
[EventGetDestName](/reference/Func/EventGetDestName)
[EventQueueGet](/reference/Func/EventQueueGet)
[EVENT_DATA](/reference/Data/EVENT_DATA)
[EVT_xxx](/reference/Symb/EVT_xxx)
[SEV_xxx](/reference/Symb/SEV_xxx)
---
