##### Data Type : Network Send and Receive
##### SESSIONID - Session ID for a network link.
---
```
#include <net.h>
```

**Definition :**
```
typedef struct {
   WORD Index; /* Index */
   WORD SeqNo; /* Sequence number */
} SESSIONID;
```

**Description :**

A SESSIONID is returned from NetLink after making a call to a remote system and establishing a character mode connection.  NetLink binds this network link to a SessionID and returns this session ID for use in subsequent calls to NetSetSessionMode, NetSend, NetReceive, and NetCloseSession.


**See Also :**
[NetLink](/domino-c-api-docs/reference/Func/NetLink)
[NetSetSessionMode](/domino-c-api-docs/reference/Func/NetSetSessionMode)
[NetSend](/domino-c-api-docs/reference/Func/NetSend)
[NetReceive](/domino-c-api-docs/reference/Func/NetReceive)
[NetCloseSession](/domino-c-api-docs/reference/Func/NetCloseSession)
---
