##### Data Type : Handles
##### MQHANDLE - A handle to a message queue.
---
```
#include <mq.h>
```
**Description :**

An MQHANDLE is a handle to a message queue, which one gets by calling MQOpen. 
The MQHANDLE returned by MQOpen may then be used by subsequent calls to the 
other message queue functions to refer to a particular queue.

**See Also :**
[MQClose](/reference/Func/MQClose)
[MQGet](/reference/Func/MQGet)
[MQIsQuitPending](/reference/Func/MQIsQuitPending)
[MQOpen](/reference/Func/MQOpen)
[MQPut](/reference/Func/MQPut)
[MQPutQuitMsg](/reference/Func/MQPutQuitMsg)
[MQScan](/reference/Func/MQScan)
---
