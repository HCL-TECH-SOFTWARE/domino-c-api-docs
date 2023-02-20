##### Function : Events
##### EventQueueFree - Destroy an event queue.
---
```
#include <event.h>
void LNPUBLIC EventQueueFree(

	char far *QueueName);
```
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
[EventQueueAlloc](/reference/Func/EventQueueAlloc)
[EventQueuePut](/reference/Func/EventQueuePut)
[EventQueueGet](/reference/Func/EventQueueGet)
[EventRegisterEventRequest](/reference/Func/EventRegisterEventRequest)
[EventDeregisterEventRequest](/reference/Func/EventDeregisterEventRequest)
[EventGetDestName](/reference/Func/EventGetDestName)
---
