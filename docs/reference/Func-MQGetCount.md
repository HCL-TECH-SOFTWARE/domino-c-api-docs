##### Function : Message Queues
##### MQGetCount - Get the number of messages in the message queue.
---
##### #include <mq.h>
WORD LNPUBLIC **MQGetCount(**

	MQHANDLE  Queue);
**Description :**
Return the number of messages waiting in the message queue.
**Parameters :**
Input :
Queue  -  Handle of an open message queue.

Output :
(routine)  -  Number of messages in the message queue.


**See Also :**
[MQClose](D:/md_files/MQClose.md)
[MQCreate](D:/md_files/MQCreate.md)
[MQGet](D:/md_files/MQGet.md)
[MQOpen](D:/md_files/MQOpen.md)
[MQPut](D:/md_files/MQPut.md)
[MQScan](D:/md_files/MQScan.md)
[MQ_MAX_MSGSIZE](D:/md_files/MQ_MAX_MSGSIZE.md)
---
