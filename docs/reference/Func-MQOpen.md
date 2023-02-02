##### Function : Message Queues
##### MQOpen - Open a message queue.
---
##### #include <mq.h>
STATUS LNPUBLIC **MQOpen(**

	const char far *QueueName,
	DWORD  Options,
	MQHANDLE far *RetQueue);
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
[MQClose](D:/md_files/MQClose.md)
[MQCreate](D:/md_files/MQCreate.md)
[MQGet](D:/md_files/MQGet.md)
[MQHANDLE](D:/md_files/MQHANDLE.md)
[MQIsQuitPending](D:/md_files/MQIsQuitPending.md)
[MQPut](D:/md_files/MQPut.md)
[MQPutQuitMsg](D:/md_files/MQPutQuitMsg.md)
[MQScan](D:/md_files/MQScan.md)
[MQSCAN_CALLBACK](D:/md_files/MQSCAN_CALLBACK.md)
[MQ_xxx (Open)](D:/md_files/MQ_xxx (Open).md)
---
