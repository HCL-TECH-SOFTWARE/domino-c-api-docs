##### Function : Mail Gateway
##### MailBroadcastNewMail - Broadcasts a new mail datagram to client workstations.
---
```
#include <mailserv.h>
void LNPUBLIC MailBroadcastNewMail(

	char far *UserName);
```
**Description :**

This function broadcasts a Notes Release 2 new mail datagram to Notes Release 2 
client workstations.  The server must be configured to support the 
"V2_Mail_Broadcast" feature.

**Parameters :**
Input :
UserName  -  Full user name string pointer (ASCIZ).



**See Also :**
---
