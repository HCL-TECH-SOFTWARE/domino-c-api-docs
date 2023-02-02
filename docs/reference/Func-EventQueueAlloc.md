##### Function : Events
##### EventQueueAlloc - Create an event queue.
---
##### #include <event.h>
STATUS LNPUBLIC **EventQueueAlloc(**

	char far *QueueName);
**Description :**
Create an event queue with the given name, to be used by user-defined event 
consumers and user-defined event producers.  Each event consumer must call 
EventQueueAlloc at startup.

Use EventQueueFree to delete the event queue and deallocate the memory 
associated with it.
**Parameters :**
Input :
QueueName  -  pointer to a null-terminated character string specifying the name to be assigned to this queue.  Maximum length of QueueName (including null terminator) is 32 characters.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


**See Also :**
[EventQueueFree](D:/md_files/EventQueueFree.md)
[EventQueuePut](D:/md_files/EventQueuePut.md)
[EventQueueGet](D:/md_files/EventQueueGet.md)
[EventRegisterEventRequest](D:/md_files/EventRegisterEventRequest.md)
[EventDeregisterEventRequest](D:/md_files/EventDeregisterEventRequest.md)
[EventGetDestName](D:/md_files/EventGetDestName.md)
---
