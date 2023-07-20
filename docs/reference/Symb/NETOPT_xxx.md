##### Symbolic Value : Network
##### NETOPT_xxx - Option flags for Network send and receive functions.
---
```
#include <net.h>
```

**Symbolic Values :**

	NETOPT_SEND_NOW	  -  Option for NetSend. Indicates that data should be transmitted immediately. Omission of this flag allows data to be buffered without necessarily being sent. However, buffered data may be sent at anytime at the discretion of NetSend (or NetReceive).

	NETOPT_FLUSH	  -  Option for NetSend. Indicates that any buffered data (to be sent or received) should be flushed before this send commences.

	NETOPT_WAIT_FOR_SOME_DATA	  -  Option for NetReceive. Waits until some data is available and returns as soon as some data is available.

	NETOPT_WAIT_FOR_ALL_DATA	  -  Option for NetReceive. Waits until the specified amount of data is received. Not to be OR'd with NETOPT_PEEK_AT_DATA.

	NETOPT_PEEK_AT_DATA	  -  Option for NetReceive. Peek at the data without actually removing it from the input stream. Not to be OR'd with NETOPT_WAIT_FOR_ALL_DATA.

	NETOPT_STREAM_MODE	  -  Option for NetSetSessionMode. Places session into stream mode. The absence of this flag places session into message mode.


**Description :**

These option flags are used with the Network send and receive functions.<br>
<br>
Unless indicated otherwise, the option flags that are appropriate for a function may be or'd together (bitwise).


**See Also :**
[NetSend](/domino-c-api-docs/reference/Func/NetSend)
[NetReceive](/domino-c-api-docs/reference/Func/NetReceive)
[NetSetSessionMode](/domino-c-api-docs/reference/Func/NetSetSessionMode)
---
