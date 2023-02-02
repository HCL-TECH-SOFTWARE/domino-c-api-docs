##### Function : Message Queues
##### MQClose - Close a message queue.
---
##### #include <mq.h>
STATUS LNPUBLIC **MQClose(**

	MQHANDLE  Queue,
	DWORD  Options);
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
[MQCreate](D:/md_files/MQCreate.md)
[MQGet](D:/md_files/MQGet.md)
[MQHANDLE](D:/md_files/MQHANDLE.md)
[MQIsQuitPending](D:/md_files/MQIsQuitPending.md)
[MQOpen](D:/md_files/MQOpen.md)
[MQPut](D:/md_files/MQPut.md)
[MQPutQuitMsg](D:/md_files/MQPutQuitMsg.md)
[MQScan](D:/md_files/MQScan.md)
[MQSCAN_CALLBACK](D:/md_files/MQSCAN_CALLBACK.md)
---
