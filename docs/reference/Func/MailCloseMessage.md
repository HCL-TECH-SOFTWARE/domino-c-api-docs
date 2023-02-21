##### Function : Mail Gateway
##### MailCloseMessage - Frees the in-memory copy of a message.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailCloseMessage(

	DHANDLE  hMessage);
```
**Description :**

This function frees the in-memory copy of a message.  If the message had file 
attachments, the attachments are freed as well.  This function should always be 
called after a gateway has finished with a message obtained with either 
MailCreateMessage or MailOpenMessage.

**Parameters :**
Input :
hMessage  -  Open message handle.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[MailCreateMessage](/domino-c-api-docs/reference/Func/MailCreateMessage)
[MailOpenMessage](/domino-c-api-docs/reference/Func/MailOpenMessage)
---
