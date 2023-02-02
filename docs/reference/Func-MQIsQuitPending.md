##### Function : Message Queues
##### MQIsQuitPending - Test whether the specified message queue is in a QUIT state.
---
##### #include <mq.h>
BOOL LNPUBLIC **MQIsQuitPending(**

	MQHANDLE  Queue);
**Description :**
This function tests whether the specified message queue is in a QUIT state, and 
returns TRUE if so. Otherwise, it returns FALSE.
**Parameters :**
Input :
Queue  -  The handle of the message queue to check.

Output :
(routine)  -  TRUE if the specified message queue is in a QUIT state, FALSE otherwise.


**See Also :**
[MQClose](D:/md_files/MQClose.md)
[MQCreate](D:/md_files/MQCreate.md)
[MQGet](D:/md_files/MQGet.md)
[MQHANDLE](D:/md_files/MQHANDLE.md)
[MQOpen](D:/md_files/MQOpen.md)
[MQPut](D:/md_files/MQPut.md)
[MQPutQuitMsg](D:/md_files/MQPutQuitMsg.md)
[MQScan](D:/md_files/MQScan.md)
[MQSCAN_CALLBACK](D:/md_files/MQSCAN_CALLBACK.md)
---
