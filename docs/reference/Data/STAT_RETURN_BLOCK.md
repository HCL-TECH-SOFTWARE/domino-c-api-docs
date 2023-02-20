##### Data Type : Statistics Reporting
##### STAT_RETURN_BLOCK - Message returned by the Collector.
---
```
#include <stats.h>
```
**Description :**

This is the structure of a message returned by the Collector in a response to a 
request made by the application.  The return message is put on the 
application's message queue.

The hStatName member of this structure is a formatted buffer containing the 
requested statistics information.  See the Message Queues chapter in the User 
Guide for details on how to parse this buffer.

**See Also :**
[MQGet](/reference/Func/MQGet)
[MQPut](/reference/Func/MQPut)
[SERVER_MSG_BLOCK](/reference/Data/SERVER_MSG_BLOCK)
---
