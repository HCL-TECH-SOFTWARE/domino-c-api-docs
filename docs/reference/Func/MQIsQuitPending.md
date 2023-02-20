##### Function : Message Queues
##### MQIsQuitPending - Test whether the specified message queue is in a QUIT state.
---
```
#include <mq.h>
BOOL LNPUBLIC MQIsQuitPending(

	MQHANDLE  Queue);
```
**Description :**

This function tests whether the specified message queue is in a QUIT state, and 
returns TRUE if so. Otherwise, it returns FALSE.

**Parameters :**
Input :
Queue  -  The handle of the message queue to check.

Output :
(routine)  -  TRUE if the specified message queue is in a QUIT state, FALSE otherwise.



**See Also :**
[MQClose](/reference/Func/MQClose)
[MQCreate](/reference/Func/MQCreate)
[MQGet](/reference/Func/MQGet)
[MQHANDLE](/reference/Data/MQHANDLE)
[MQOpen](/reference/Func/MQOpen)
[MQPut](/reference/Func/MQPut)
[MQPutQuitMsg](/reference/Func/MQPutQuitMsg)
[MQScan](/reference/Func/MQScan)
[MQSCAN_CALLBACK](/reference/Data/MQSCAN_CALLBACK)
---
