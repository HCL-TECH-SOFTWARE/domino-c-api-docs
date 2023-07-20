##### Data Type : Handles
##### MQHANDLE - A handle to a message queue.
---
```
#include <mq.h>
```

**Definition :**
```
typedef DWORD MQHANDLE;
```

**Description :**

An MQHANDLE is a handle to a message queue, which one gets by calling MQOpen. The MQHANDLE returned by MQOpen may then be used by subsequent calls to the other message queue functions to refer to a particular queue.


**See Also :**
[MQClose](/domino-c-api-docs/reference/Func/MQClose)
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[MQIsQuitPending](/domino-c-api-docs/reference/Func/MQIsQuitPending)
[MQOpen](/domino-c-api-docs/reference/Func/MQOpen)
[MQPut](/domino-c-api-docs/reference/Func/MQPut)
[MQPutQuitMsg](/domino-c-api-docs/reference/Func/MQPutQuitMsg)
[MQScan](/domino-c-api-docs/reference/Func/MQScan)
---
