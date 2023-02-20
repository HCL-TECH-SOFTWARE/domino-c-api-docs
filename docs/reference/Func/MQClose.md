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
[MQCreate](/reference/Func/MQCreate)
[MQGet](/reference/Func/MQGet)
[MQHANDLE](/reference/Data/MQHANDLE)
[MQIsQuitPending](/reference/Func/MQIsQuitPending)
[MQOpen](/reference/Func/MQOpen)
[MQPut](/reference/Func/MQPut)
[MQPutQuitMsg](/reference/Func/MQPutQuitMsg)
[MQScan](/reference/Func/MQScan)
[MQSCAN_CALLBACK](/reference/Data/MQSCAN_CALLBACK)
---
