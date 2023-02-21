##### Function : Message Queues
##### MQPutQuitMsg - Adds a QUIT message to the message queue.
---
```
#include <mq.h>
void LNPUBLIC MQPutQuitMsg(

	MQHANDLE  Queue);
```
**Description :**

This function puts the message queue in a QUIT state, which indicates to 
applications that read the message queue that they should terminate. 

**Parameters :**
Input :
Queue  -  The handle of message queue that will receive the QUIT message.

Output :
(routine)  -  None.



**See Also :**
[MQHANDLE](/domino-c-api-docs/reference/Data/MQHANDLE)
---
