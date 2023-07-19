##### Data Type : Statistics Reporting
##### STAT_RETURN_BLOCK - Message returned by the Collector.
---
```
#include <stats.h>
```

**Definition :**

typedef struct {
   char   StatName[MAXSPRINTF];   
   DHANDLE hStatName;   
   DWORD  StatNameSize;   
   char   ServerName[MAXPATH];   
   STATUS error;       
} STAT_RETURN_BLOCK;

**Description :**

This is the structure of a message returned by the Collector in a response to a request made by the application.  The return message is put on the application's message queue.<br>

<ul>The hStatName member of this structure is a formatted buffer containing the requested statistics information.  See the Message Queues chapter in the <i>User Guide</i> for details on how to parse this buffer.</ul>



**See Also :**
[MQGet](/domino-c-api-docs/reference/Func/MQGet)
[MQPut](/domino-c-api-docs/reference/Func/MQPut)
[SERVER_MSG_BLOCK](/domino-c-api-docs/reference/Data/SERVER_MSG_BLOCK)
---
