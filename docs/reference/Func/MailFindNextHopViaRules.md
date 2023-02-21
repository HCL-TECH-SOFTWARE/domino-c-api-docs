##### Function : Mail Gateway
##### MailFindNextHopViaRules - Find next hop to recipient using domain routing rules.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailFindNextHopViaRules(

	DHANDLE  hTables,
	char far *RecipientAddress,
	char far *retDestServer,
	char far *retDestDomain);
```
**Description :**

Given a handle to a set of routing tables and the distinguished name of the 
desired recipient, obtain either the server name or domain name for the next 
hop.

**Parameters :**
Input :
hTables  -  Handle to routing tables to search.

RecipientAddress  -  Null-terminated string containing the distinguished name of the recipient.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Next hop located.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 


retDestServer  -  If the destination is a server, the null-terminated name of that server.  If the destination is a domain, this is set to the empty string ("").  The maximum length (in bytes) for this parameter is MAXUSERNAME.

retDestDomain  -  If the destination is a domain, the null-terminated name of that domain.  If the destination is a server, this is set to the empty string ("").  The maximum length (in bytes) for this parameter is MAXDOMAINPATH.


**See Also :**
[MailLoadRoutingTables](/domino-c-api-docs/reference/Func/MailLoadRoutingTables)
[MailReloadRoutingTables](/domino-c-api-docs/reference/Func/MailReloadRoutingTables)
[MailUnloadRoutingTables](/domino-c-api-docs/reference/Func/MailUnloadRoutingTables)
---
