##### Data Type : Message Queues
##### MQSCAN_CALLBACK - Action routine invoked by MQScan().
---
```
#include <mq.h>
```
**Description :**

This type defines the prototype of the user-written callback routine that will 
be invoked by the function MQScan() for each message in a message queue. The 
address of a routine with this prototype is supplied as an argument to 
MQScan(). 

The Action routine may return one of the following values to affect the 
behavior of MQScan:

NOERROR - process the next message.
ERR_MQSCAN_ABORT - return from MQScan immediately without dequeueing a 
message.  Note that MQScan returns ERR_MQSCAN_ABORT.
ERR_MQSCAN_DEQUEUE - remove the message from the queue, terminate the 
enumeration, and return the current message to the caller of MQScan.  If the 
Buffer is smaller than the message, MQScan can return ERR_MQ_BFR_TOO_SMALL.
ERR_MQSCAN_DELETE - remove the current message from the message queue and 
continue the enumeration.

The arguments to the MQSCAN_CALLBACK are as follows:

pBuffer - a pointer to a buffer containing the current message.
Length  - the length of the message in the buffer.
Priority  - the priority of this message, from 1(highest) to MAXWORD (lowest).
Ctx       - a pointer to user-defined data. This allows non-global data to be 
shared between MQScan() and the callback function.

Under Windows, the action routine must be present in an EXPORT statement in the 
application's .DEF file. 


**See Also :**
[MQScan](/domino-c-api-docs/reference/Func/MQScan)
---
