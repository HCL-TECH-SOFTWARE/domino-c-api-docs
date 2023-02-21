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
[MQClose](/domino-c-api-docs/reference/Func/MQClose)
[MQCreate](/domino-c-api-docs/reference/Func/MQCreate)
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[MQHANDLE](/domino-c-api-docs/reference/Data/MQHANDLE)
[MQOpen](/domino-c-api-docs/reference/Func/MQOpen)
[MQPut](/domino-c-api-docs/reference/Func/MQPut)
[MQPutQuitMsg](/domino-c-api-docs/reference/Func/MQPutQuitMsg)
[MQScan](/domino-c-api-docs/reference/Func/MQScan)
[MQSCAN_CALLBACK](/domino-c-api-docs/reference/Data/MQSCAN_CALLBACK)
---
