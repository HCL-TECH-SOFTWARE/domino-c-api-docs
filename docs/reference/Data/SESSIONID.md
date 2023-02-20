##### Data Type : Network Send and Receive
##### SESSIONID - Session ID for a network link.
---
```
#include <net.h>
```
**Description :**

A SESSIONID is returned from NetLink after making a call to a remote system and 
establishing a character mode connection.  NetLink binds this network link to a 
SessionID and returns this session ID for use in subsequent calls to 
NetSetSessionMode, NetSend, NetReceive, and NetCloseSession.

**See Also :**
[NetLink](/reference/Func/NetLink)
[NetSetSessionMode](/reference/Func/NetSetSessionMode)
[NetSend](/reference/Func/NetSend)
[NetReceive](/reference/Func/NetReceive)
[NetCloseSession](/reference/Func/NetCloseSession)
---
