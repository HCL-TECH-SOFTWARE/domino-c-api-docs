##### Function : Message Queues
##### MQPut - Adds a message to the specified message queue.
---
```
#include <mq.h>
STATUS LNPUBLIC MQPut(

	MQHANDLE  Queue,
	WORD  Priority,
	char far *Buffer,
	WORD  Length,
	DWORD  Options);
```
**Description :**

This function adds a message to the specified message queue. The message will 
be placed in the queue according to the value of its priority argument - higher 
priority messages will be enqueued ahead of lower priority messages.

If the queue is full or in a QUIT state, the message will not be put in the 
queue, and the function will return an appropriate error code.

**Parameters :**
Input :
Queue  -  The handle of the queue that will receive the message.

Priority  -  The priority of this message. See xxxPRIORITY.

Buffer  -  A pointer to the buffer containing the message.  Maximum buffer length is MQ_MAX_MSGSIZE.

Length  -  Length of the message in bytes.

Options  -  Reserved. Must be 0.

Output :
(routine)  -  NOERROR
ERR_MQ_EMPTY - The specified queue is either empty or not a valid message queue.
ERR_MQ_QUITTING - The queue's quit flag is set.
ERR_MQ_EXCEEDED_QUOTA - The message queue is full and cannot take another message.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.



**See Also :**
[MQClose](/domino-c-api-docs/reference/Func/MQClose)
[MQCreate](/domino-c-api-docs/reference/Func/MQCreate)
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[MQHANDLE](/domino-c-api-docs/reference/Data/MQHANDLE)
[MQIsQuitPending](/domino-c-api-docs/reference/Func/MQIsQuitPending)
[MQOpen](/domino-c-api-docs/reference/Func/MQOpen)
[MQPutQuitMsg](/domino-c-api-docs/reference/Func/MQPutQuitMsg)
[MQScan](/domino-c-api-docs/reference/Func/MQScan)
[MQ_MAX_MSGSIZE](/domino-c-api-docs/reference/Symb/MQ_MAX_MSGSIZE)
[MQ_xxx (Get)](/domino-c-api-docs/reference/Symb/MQ_xxx (Get))
[MQ_xxx (Open)](/domino-c-api-docs/reference/Symb/MQ_xxx (Open))
---
