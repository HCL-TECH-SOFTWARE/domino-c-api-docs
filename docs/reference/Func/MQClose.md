##### Function : Message Queues
##### MQClose - Close a message queue.
---
```
#include <mq.h>
STATUS LNPUBLIC MQClose(

	MQHANDLE  Queue,
	DWORD  Options);
```
**Description :**

This function will decrement a message queue's reference count. If the 
reference count equals 0, the memory for the message queue is freed.

**Parameters :**
Input :
Queue  -  The handle of the message queue that is to be closed.

Options  -  Reserved. Must be 0.

Output :
(routine)  -  NOERROR
ERR_MQ_EMPTY - The MQHANDLE passed into this routine was not a valid MQHANDLE.



**See Also :**
[MQCreate](/domino-c-api-docs/reference/Func/MQCreate)
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[MQHANDLE](/domino-c-api-docs/reference/Data/MQHANDLE)
[MQIsQuitPending](/domino-c-api-docs/reference/Func/MQIsQuitPending)
[MQOpen](/domino-c-api-docs/reference/Func/MQOpen)
[MQPut](/domino-c-api-docs/reference/Func/MQPut)
[MQPutQuitMsg](/domino-c-api-docs/reference/Func/MQPutQuitMsg)
[MQScan](/domino-c-api-docs/reference/Func/MQScan)
[MQSCAN_CALLBACK](/domino-c-api-docs/reference/Data/MQSCAN_CALLBACK)
---
