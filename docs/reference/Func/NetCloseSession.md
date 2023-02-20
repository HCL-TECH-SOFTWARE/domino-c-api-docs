##### Function : Network Send and Receive
##### NetCloseSession - Closes a network session.
---
```
#include <net.h>
void LNPUBLIC NetCloseSession(

	SESSIONID  SessionID);
```
**Description :**

This function closes a network session.  If a phone call had been made (by 
NetLink) in order to create that session, the phone call is hung up by 
NetCloseSession.

**Parameters :**
Input :
SessionID  -  A Session ID obtained in a previous call to NetLink.

Output :
(routine)  -  None



**See Also :**
[NetLink](/reference/Func/NetLink)
---
