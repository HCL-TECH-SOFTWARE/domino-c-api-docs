##### Function : Events
##### EventQueuePut - Place an event in an event queue.
---
##### #include <event.h>
STATUS LNPUBLIC **EventQueuePut(**

	char far *QueueName,
	char far *Originating Server,
	WORD  Type,
	WORD  Severity,
	TIMEDATE far *EventTime,
	WORD  FormatSpecifier,
	WORD  EventDataLength,
	void far *EventSpecificData);
**Description :**
An event producer calls EventQueuePut to place an event in an event queue. The 
parameter EventSpecificData may be used to pass user-defined data to the event 
consumer.

Each different combination of type and severity defines a distinct event, so a 
fairly large number of distinct events can be handled.

Note: The names of the event type flags (EVT_xxx) and the event severity flags 
(SEV_xxx) are descriptive of how Domino uses events. An event producer writing 
to a user-defined event queue  is not required to follow this convention.   In 
other words, if a user is not interested in anything relating to mail, the 
event type EVT_MAIL may be used to signal some other type of occurrence.

A user might even want to re-map the event type names (defined in EVT_xxx)  and 
event severity names (defined in SEV_xxx) to have names that are more relevant 
to their tasks by doing something like:

#define   User_Defined_Event_1    EVT_MAIL

**Parameters :**
Input :
QueueName  -  Far pointer to a null-terminated character string containing the name of the queue that will receive the event.  Some internal queue names are defined in EVENT_XXXX_QUEUE_NAME.

Originating Server  -  Far pointer to a null-terminated character string containing the name of the server on which the event occurred.  If NULL, uses the current server name.  

Type  -  The type of event.  See the definition of EVT_xxx for a list of valid values for this parameter. 

Severity  -  The severity of the event.  See the definition of SEV_xxx for a list of valid values for this parameter.

EventTime  -  The time at which the event is generated.

FormatSpecifier  -  The format of the data specific to this event.  See FMT_XXX for Valid format specifier flags.

EventDataLength  -  The length of the data specific to this event.

EventSpecificData  -  A far pointer to the first byte of data that is specific to this event.  This data block is user-defined.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.




**See Also :**
[EventDeregisterEventRequest](D:/md_files/EventDeregisterEventRequest.md)
[EventGetDestName](D:/md_files/EventGetDestName.md)
[EventQueueAlloc](D:/md_files/EventQueueAlloc.md)
[EventQueueFree](D:/md_files/EventQueueFree.md)
[EventQueueGet](D:/md_files/EventQueueGet.md)
[EventRegisterEventRequest](D:/md_files/EventRegisterEventRequest.md)
[EVENT_XXX_QUEUE_NAME](D:/md_files/EVENT_XXX_QUEUE_NAME.md)
[EVT_xxx](D:/md_files/EVT_xxx.md)
[FMT_xxx](D:/md_files/FMT_xxx.md)
[SEV_xxx](D:/md_files/SEV_xxx.md)
---
