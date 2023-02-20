##### Function : Message Queues
##### MQGetCount - Get the number of messages in the message queue.
---
```
#include <mq.h>
WORD LNPUBLIC MQGetCount(

	MQHANDLE  Queue);
```
**Description :**

Return the number of messages waiting in the message queue.

**Parameters :**
Input :
Queue  -  Handle of an open message queue.

Output :
(routine)  -  Number of messages in the message queue.



**See Also :**
[MQClose](/reference/Func/MQClose)
[MQCreate](/reference/Func/MQCreate)
[MQGet](/reference/Func/MQGet)
[MQOpen](/reference/Func/MQOpen)
[MQPut](/reference/Func/MQPut)
[MQScan](/reference/Func/MQScan)
[MQ_MAX_MSGSIZE](/reference/Symb/MQ_MAX_MSGSIZE)
---
