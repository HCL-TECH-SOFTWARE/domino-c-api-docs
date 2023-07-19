##### Symbolic Value : Message Queues
##### xxxPRIORITY - Signifies the message priority in a message queue.
---
```
#include <mq.h>
```

**Symbolic Values :**

	NOPRIORITY	  -  This symbolic value defines the lowest priority assignable to a message in a message queue. Specifying NOPRIORITY as the Priority argument in a call to MQPut() means that the message has no priority at all, and should be placed at the end of the message queue. This avoids the need for MQPut() to perform a linear search in order to find the correct position for this message.

	LOWPRIORITY	  -  This symbolic value defines the lowest priority assignable to a message in a message queue. Same as NOPRIORITY.

	HIGHPRIORITY	  -  This symbolic value defines the highest priority assignable to a message in a message queue.


**Description :**

These symbolic values defines the priorities assignable to a message in a message queue.


**See Also :**
[MQPut](/domino-c-api-docs/reference/Func/MQPut)
---
