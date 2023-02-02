##### Function : Events
##### EventQueueFree - Destroy an event queue.
---
##### #include <event.h>
void LNPUBLIC **EventQueueFree(**

	char far *QueueName);
**Description :**
Destroy the event queue with the given name and deallocate the memory 
associated with it.  EventQueueFree is called at shutdown time by each event 
consumer.
**Parameters :**
Input :
QueueName  -  pointer to a null-terminated character string containing the name of the queue to be destroyed.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.




**See Also :**
[EventQueueAlloc](D:/md_files/EventQueueAlloc.md)
[EventQueuePut](D:/md_files/EventQueuePut.md)
[EventQueueGet](D:/md_files/EventQueueGet.md)
[EventRegisterEventRequest](D:/md_files/EventRegisterEventRequest.md)
[EventDeregisterEventRequest](D:/md_files/EventDeregisterEventRequest.md)
[EventGetDestName](D:/md_files/EventGetDestName.md)
---
