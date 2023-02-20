##### Function : Extension Manager
##### SMTPDisconnectEMCallback - Extension Manager callback for EM_SMTPDISCONNECT
---
```
#include <extmgr.h>
STATUS LNPUBLIC SMTPDisconnectEMCallback(

	DWORD  SessionID);
```
**Description :**

EM_SMTPDISCONNECT is called when a SMTP connection is being torn down.  This 
includes normal and abnormal disconnects, such as when the QUIT command is 
issued or when a session times out.

**Parameters :**
Input :
SessionID  -  Unique session identifier.

Output :
(routine)  -  Return status from the call 
ERR_EM_CONTINUE, any other value will have no affect on Domino internal processing.



**See Also :**
[EM_xxx](/reference/Symb/EM_xxx)
---
