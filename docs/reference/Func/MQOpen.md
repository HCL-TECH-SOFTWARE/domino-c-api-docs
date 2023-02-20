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
[MQClose](/reference/Func/MQClose)
[MQCreate](/reference/Func/MQCreate)
[MQGet](/reference/Func/MQGet)
[MQHANDLE](/reference/Data/MQHANDLE)
[MQIsQuitPending](/reference/Func/MQIsQuitPending)
[MQPut](/reference/Func/MQPut)
[MQPutQuitMsg](/reference/Func/MQPutQuitMsg)
[MQScan](/reference/Func/MQScan)
[MQSCAN_CALLBACK](/reference/Data/MQSCAN_CALLBACK)
[MQ_xxx (Open)](/reference/Symb/MQ_xxx (Open))
---
