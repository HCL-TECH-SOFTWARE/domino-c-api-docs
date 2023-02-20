##### Function : Message Queues
##### MQScan - Call action routine for each message in a message queue.
---
```
#include <mq.h>
STATUS LNPUBLIC MQScan(

	MQHANDLE  Queue,
	char far *Buffer,
	WORD  BufLength,
	DWORD  Options,
	MQSCAN_CALLBACK  ActionRoutine,
	void far *Ctx,
	WORD far *retMsgLength);
```
**Description :**

This function parses a message queue, calling an action routine for each 
message in the queue.  If the message queue is empty, or if all messages in the 
queue have been enumerated without returning an error code, MQScan returns 
ERR_MQ_EMPTY.  In the simple case, MQScan() does not modify the contents of the 
queue;  by returning the appropriate error codes to MQScan, the action routine 
can specify that messages are to be removed from the queue or skipped, or that 
enumeration is to be terminated immediately.  See the reference entry for 
MQSCAN_CALLBACK for more details.

Note: MQScan locks out all other message queue function calls until it 
completes.

**Parameters :**
Input :
Queue  -  The handle of the queue to be enumerated.

Buffer  -  Pointer to a buffer in which to store the retrieved message.  Set this to NULL if you just wish to dequeue and discard a message.

BufLength  -  Size in bytes of the buffer that will receive the message.

Options  -  Reserved. Must be 0.

ActionRoutine  -  A pointer to an action routine to be called for each message in a message queue. The routine must match the function prototype defined my MQSCAN_CALLBACK.

Ctx  -  A pointer to user-defined data.  This pointer is then passed to the Action Routine.  It provides a way to pass non-global data to the Action Routine.

Output :
(routine)  -  NOERROR
ERR_MQ_EMPTY - The specified message queue is empty, not a message queue, or all messages in the queue have been enumerated without error.
ERR_MQ_QUITTING - The queue's quit flag is set, and no enumeration has occurred.
ERR_MQSCAN_ABORT - The action routine returned the error code MQSCAN_ABORT to MQScan. This indicates that the action routine chose to abort the enumeration without dequeueing the current message.
ERR_MQ_BFR_TOO_SMALL - The message being read is larger than the buffer supplied, so the message was truncated.


Buffer  -  Pointer to the buffer that received the message.  The message will be truncated if the buffer is too small for the message. 

Ctx  -  

retMsgLength  -  The number of bytes written to the buffer.


**See Also :**
[MQClose](/reference/Func/MQClose)
[MQCreate](/reference/Func/MQCreate)
[MQGet](/reference/Func/MQGet)
[MQHANDLE](/reference/Data/MQHANDLE)
[MQIsQuitPending](/reference/Func/MQIsQuitPending)
[MQOpen](/reference/Func/MQOpen)
[MQPut](/reference/Func/MQPut)
[MQPutQuitMsg](/reference/Func/MQPutQuitMsg)
[MQScan](/reference/Func/MQScan)
[MQSCAN_CALLBACK](/reference/Data/MQSCAN_CALLBACK)
[MQ_xxx (Get)](/reference/Symb/MQ_xxx (Get))
[MQ_xxx (Open)](/reference/Symb/MQ_xxx (Open))
---
