##### Function : Message Queues
##### MQPut - Adds a message to the specified message queue.
---
##### #include <mq.h>
STATUS LNPUBLIC **MQPut(**

	MQHANDLE  Queue,
	WORD  Priority,
	char far *Buffer,
	WORD  Length,
	DWORD  Options);
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
[MQClose](D:/md_files/MQClose.md)
[MQCreate](D:/md_files/MQCreate.md)
[MQGet](D:/md_files/MQGet.md)
[MQHANDLE](D:/md_files/MQHANDLE.md)
[MQIsQuitPending](D:/md_files/MQIsQuitPending.md)
[MQOpen](D:/md_files/MQOpen.md)
[MQPutQuitMsg](D:/md_files/MQPutQuitMsg.md)
[MQScan](D:/md_files/MQScan.md)
[MQ_MAX_MSGSIZE](D:/md_files/MQ_MAX_MSGSIZE.md)
[MQ_xxx (Get)](D:/md_files/MQ_xxx (Get).md)
[MQ_xxx (Open)](D:/md_files/MQ_xxx (Open).md)
---
