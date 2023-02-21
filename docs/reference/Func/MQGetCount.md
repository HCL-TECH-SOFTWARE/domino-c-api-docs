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
[MQClose](/domino-c-api-docs/reference/Func/MQClose)
[MQCreate](/domino-c-api-docs/reference/Func/MQCreate)
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[MQOpen](/domino-c-api-docs/reference/Func/MQOpen)
[MQPut](/domino-c-api-docs/reference/Func/MQPut)
[MQScan](/domino-c-api-docs/reference/Func/MQScan)
[MQ_MAX_MSGSIZE](/domino-c-api-docs/reference/Symb/MQ_MAX_MSGSIZE)
---
