##### Function : Message Queues
##### MQOpen - Open a message queue.
---
```
#include <mq.h>
STATUS LNPUBLIC MQOpen(

	const char far *QueueName,
	DWORD  Options,
	MQHANDLE far *RetQueue);
```
**Description :**

Open a message queue, get a handle to it, and increment the queue's reference 
counter. The handle is used by the functions that write to and read from the 
message queue.

**Parameters :**
Input :
QueueName  -  The name of the queue that is to be opened.

Options  -   Optional MQOpen options.  Should be 0 or see MQ_xxx (MQOpen - Options) for possible values.

Output :
(routine)  -  
NOERROR
ERR_NO_SUCH_MQ - No message queue with the specified name exists.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



RetQueue  -  A pointer to message queue's handle.


**See Also :**
[MQClose](/domino-c-api-docs/reference/Func/MQClose)
[MQCreate](/domino-c-api-docs/reference/Func/MQCreate)
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[MQHANDLE](/domino-c-api-docs/reference/Data/MQHANDLE)
[MQIsQuitPending](/domino-c-api-docs/reference/Func/MQIsQuitPending)
[MQPut](/domino-c-api-docs/reference/Func/MQPut)
[MQPutQuitMsg](/domino-c-api-docs/reference/Func/MQPutQuitMsg)
[MQScan](/domino-c-api-docs/reference/Func/MQScan)
[MQSCAN_CALLBACK](/domino-c-api-docs/reference/Data/MQSCAN_CALLBACK)
[MQ_xxx (Open)](/domino-c-api-docs/reference/Symb/MQ_xxx (Open))
---
