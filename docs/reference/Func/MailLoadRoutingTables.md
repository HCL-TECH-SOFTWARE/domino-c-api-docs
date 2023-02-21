##### Function : Mail Gateway
##### MailLoadRoutingTables - Load routing tables from the Domino Directory (Server's Address book).
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailLoadRoutingTables(

	DBHANDLE  hAddressBook,
	char far *LocalServerName,
	char far *LocalDomainDomain,
	char far *TaskName,
	BOOL  EnableTrace,
	BOOL  EnableDebug,
	DHANDLE far *rethTables);
```
**Description :**

Load the set of routing tables from the Domino Directory (Server's Address 
book) into memory.  The caller is responsible for freeing memory used for the 
routing tables by calling MailUnloadRoutingTables ().

**Parameters :**
Input :
hAddressBook  -  Handle to the open Domino Directory (Server's Address book).

LocalServerName  -  Null-terminated string containing the name of the local server - the server where this function call is taking place, in upper case.

LocalDomainDomain  -  Null-terminated string containing the domain of the local server - the domain of the server where this function call is taking place.

TaskName  -  Null-terminated string containing the name of the calling task.  This string uniquely identifies the different mail routing services on a given server.

EnableTrace  -  If TRUE, tracing of mail routings is enabled.

EnableDebug  -  If TRUE, mail routing debug information is generated in the debugging log.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Routing tables loaded.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 


rethTables  -  Handle to the memory block containing the mail routing tables.  The caller must free this memory using MailUnloadRoutingTables ().


**See Also :**
[MailFindNextHopToDomain](/domino-c-api-docs/reference/Func/MailFindNextHopToDomain)
[MailFindNextHopToRecipient](/domino-c-api-docs/reference/Func/MailFindNextHopToRecipient)
[MailFindNextHopToServer](/domino-c-api-docs/reference/Func/MailFindNextHopToServer)
[MailFindNextHopViaRules](/domino-c-api-docs/reference/Func/MailFindNextHopViaRules)
[MailReloadRoutingTables](/domino-c-api-docs/reference/Func/MailReloadRoutingTables)
[MailResetAllDynamicCosts](/domino-c-api-docs/reference/Func/MailResetAllDynamicCosts)
[MailSetDynamicCost](/domino-c-api-docs/reference/Func/MailSetDynamicCost)
[MailUnloadRoutingTables](/domino-c-api-docs/reference/Func/MailUnloadRoutingTables)
[MailLoadRoutingTablesExt](/domino-c-api-docs/reference/Func/MailLoadRoutingTablesExt)
---
