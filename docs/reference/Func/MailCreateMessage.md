##### Function : Mail Gateway
##### MailCreateMessage - Creates an in-memory message.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailCreateMessage(

	DBHANDLE  hFile,
	DHANDLE far *rethMessage);
```
**Description :**

This function creates an in-memory message.  This function is usually used by 
gateways for creating inbound messages from foreign mail systems.  A handle to 
the open message is returned for use in other message object function calls.  
Use MailCloseMessage to close the message handle and deallocate the memory 
associated with it.

**Parameters :**
Input :
hFile  -  Open message file handle.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


rethMessage  -  Open message handle.


**See Also :**
[MailCloseMessage](/reference/Func/MailCloseMessage)
---
