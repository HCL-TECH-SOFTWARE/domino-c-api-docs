##### Function : Mail Gateway
##### MailSetDynamicCost - Set the dynamic cost for a server.
---
```
#include <mailserv.h>
BOOL LNPUBLIC MailSetDynamicCost(

	DHANDLE  hTables,
	char far *Server,
	SWORD  CostBias);
```
**Description :**

The mail routing tables contain an estimate of the "cost" to reach a given 
server (the amount of effort needed to transfer mail to that server).  There is 
also a "dynamic cost" value which mail gateway applications can use for minor 
adjustments to this cost value.  The dynamic cost may be -1, 0, or +1, and is 
added to the cost value for each hop when determining the best route to a given 
server.

This function sets the dynamic cost value used in determining the best route to 
the specified server.

**Parameters :**
Input :
hTables  -  Handle to the memory block containing the mail routing tables.

Server  -  Null-terminated string containing the name of the destination server.

CostBias  -  New dynamic cost value.  May be one of -1, 0, or +1.

Output :
(routine)  -  TRUE if any costs changed, FALSE if no costs changed.



**See Also :**
[MailLoadRoutingTables](/reference/Func/MailLoadRoutingTables)
[MailReloadRoutingTables](/reference/Func/MailReloadRoutingTables)
[MailResetAllDynamicCosts](/reference/Func/MailResetAllDynamicCosts)
[MailUnloadRoutingTables](/reference/Func/MailUnloadRoutingTables)
---
