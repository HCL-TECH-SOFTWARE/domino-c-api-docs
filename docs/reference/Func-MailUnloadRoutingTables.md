##### Function : Mail Gateway
##### MailUnloadRoutingTables - Unload mail routing tables from memory.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailUnloadRoutingTables(**

	DHANDLE  hTables);
**Description :**
Unload the routing tables from memory and free the memory allocated.
**Parameters :**
Input :
hTables  -  Handle to the memory block containing the mail routing tables.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is.


**See Also :**
[MailLoadRoutingTables](D:/md_files/MailLoadRoutingTables.md)
[MailReloadRoutingTables](D:/md_files/MailReloadRoutingTables.md)
---
