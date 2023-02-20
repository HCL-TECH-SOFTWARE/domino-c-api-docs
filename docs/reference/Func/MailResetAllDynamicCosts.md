##### Function : Mail Gateway
##### MailResetAllDynamicCosts - Reset all dynamic costs.
---
```
#include <mailserv.h>
BOOL LNPUBLIC MailResetAllDynamicCosts(

	DHANDLE  hTables);
```
**Description :**

The mail routing tables contain an estimate of the "cost" to reach a given 
server (the amount of effort needed to transfer mail to that server).  There is 
also a "dynamic cost" value which mail gateway applications can use for minor 
adjustments to this cost value.  The dynamic cost may be -1, 0, or +1, and is 
added to the cost value for each hop when determining the best route to a given 
server.

This function resets all the dynamic cost values to 0.

**Parameters :**
Input :
hTables  -  Handle to the memory block containing the mail routing tables.

Output :
(routine)  -  TRUE if any of the dynamic cost values were non-zero, FALSE if all were zero.



**See Also :**
[MailLoadRoutingTables](/reference/Func/MailLoadRoutingTables)
[MailReloadRoutingTables](/reference/Func/MailReloadRoutingTables)
[MailSetDynamicCost](/reference/Func/MailSetDynamicCost)
[MailUnloadRoutingTables](/reference/Func/MailUnloadRoutingTables)
---
