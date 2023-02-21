##### Function : Message Queues
##### MQCreate - Create a message queue.
---
```
#include <mq.h>
STATUS LNPUBLIC MQCreate(

	const char far *QueueName,
	WORD  Quota,
	DWORD  Options);
```
**Description :**

Create a message queue with the specified name. Message queues provide Domino 
and Notes applications with inter-process communication capabilities.  A 
subsequent call to MQOpen is required to use this message queue.

**Parameters :**
Input :
QueueName  -  A pointer to the name to be assigned to the message queue.

Quota  -  Maximum number of messages that the queue may contain. Set this to zero for the default maximum.  The default maximum number of messages that the queue may contain is MAXWORD.

Options  -  Reserved. Must be 0.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_DUPLICATE_MQ - A message queue with the specified name already exists.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.




**See Also :**
[MQClose](/domino-c-api-docs/reference/Func/MQClose)
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[MQHANDLE](/domino-c-api-docs/reference/Data/MQHANDLE)
[MQIsQuitPending](/domino-c-api-docs/reference/Func/MQIsQuitPending)
[MQOpen](/domino-c-api-docs/reference/Func/MQOpen)
[MQPut](/domino-c-api-docs/reference/Func/MQPut)
[MQPutQuitMsg](/domino-c-api-docs/reference/Func/MQPutQuitMsg)
[MQScan](/domino-c-api-docs/reference/Func/MQScan)
[MQSCAN_CALLBACK](/domino-c-api-docs/reference/Data/MQSCAN_CALLBACK)
---
