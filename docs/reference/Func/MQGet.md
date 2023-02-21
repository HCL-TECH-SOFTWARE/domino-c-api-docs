##### Function : Message Queues
##### MQGet - Read and dequeue a message from a message queue.
---
```
#include <mq.h>
STATUS LNPUBLIC MQGet(

	MQHANDLE  Queue,
	char far *Buffer,
	WORD  BufLength,
	DWORD  Options,
	DWORD  Timeout,
	WORD far *retMsgLength);
```
**Description :**

Retrieves a message from a message queue, provided the queue is not in a QUIT 
state. The message will be stored in the buffer specified in the Buffer 
argument.  
Note: The error code ERR_MQ_QUITTING indicates that the message queue is in the 
QUIT state, denoting that applications that are reading the message queue 
should terminate. For instance, a server addin's message queue will be placed 
in the QUIT state when a "tell <addin> quit" command is input at the console.

**Parameters :**
Input :
Queue  -  The handle of the queue from which to retrieve the message.

BufLength  -  Size in bytes of the buffer that will receive the message.

Options  -  0 to return immediately if the message queue is empty, MQ_WAIT_FOR_MSG to wait for a message.

Timeout  -  If Options is set to MQ_WAIT_FOR_MSG is set, the number of milliseconds to wait for a message before timing out. Specify 0 to wait forever. If the message queue goes into a QUIT state before the Timeout expires, MQGet will return immediately.

Output :
(routine)  -  NOERROR
ERR_MQ_EMPTY - The specified queue is either empty or not a valid message queue.
ERR_MQ_QUITTING - The queue's quit flag is set. 
ERR_MQ_TIMEOUT - The queue has remained empty for more than the amount of time specified in the Timeout argument.
ERR_MQ_BFR_TOO_SMALL - The message being read is larger than the buffer supplied, so the message was truncated.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


Buffer  -   Pointer to the buffer that received the message.  The message will be truncated if the buffer is too small for the message. 

retMsgLength  -  The number of bytes written to the buffer.


**See Also :**
[MQClose](/domino-c-api-docs/reference/Func/MQClose)
[MQCreate](/domino-c-api-docs/reference/Func/MQCreate)
[MQHANDLE](/domino-c-api-docs/reference/Data/MQHANDLE)
[MQIsQuitPending](/domino-c-api-docs/reference/Func/MQIsQuitPending)
[MQOpen](/domino-c-api-docs/reference/Func/MQOpen)
[MQPut](/domino-c-api-docs/reference/Func/MQPut)
[MQPutQuitMsg](/domino-c-api-docs/reference/Func/MQPutQuitMsg)
[MQScan](/domino-c-api-docs/reference/Func/MQScan)
[MQSCAN_CALLBACK](/domino-c-api-docs/reference/Data/MQSCAN_CALLBACK)
[MQ_xxx (Get)](/domino-c-api-docs/reference/Symb/MQ_xxx (Get))
---
