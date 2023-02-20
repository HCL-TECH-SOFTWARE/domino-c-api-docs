##### Function : Mail Gateway
##### MailFindNextHopToDomain - Find next hop to the destination domain.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailFindNextHopToDomain(

	DHANDLE  hTables,
	char far *OriginatorsDomain,
	char far *DestDomain,
	char far *NextHopServer,
	char far *NextHopMailbox,
	DWORD far *NextHopFlags,
	char far *ErrorServer);
```
**Description :**

Given a handle to a set of routing tables, the name of the originator's domain, 
and the name of the destination domain, obtain the server name and mailbox file 
name for the next step in routing a message to the destination domain.

Note:  This function assumes that the destination domain is not the domain for 
the local server.

**Parameters :**
Input :
hTables  -  Handle to routing tables to search.

OriginatorsDomain  -  Null-terminated string containing the name of the domain for the originator of the message.

DestDomain  -  Null-terminated string containing the name of the destination domain.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Next hop located.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user. 


NextHopServer  -  Null-terminated string containing the name of the next server to route the message to.  The maximum length (in bytes) for this parameter is MAXUSERNAME.

NextHopMailbox  -  Null-terminated string containing the mailbox file name on the next hop server.  The maximum length (in bytes) for this parameter is MAXPATH.

NextHopFlags  -  Additional flags describing the next hop server.  If NEXTHOP_INTRANET bit is set, the next hop server is on the same network as the current server.  If NEXTHOP_USESMTP bit is set, SMTP will be used to reach the next hop server.

ErrorServer  -  If no route to the specified destination domain is found, the null-terminated name of the error server is stored at this address.  The maximum length (in bytes) for this parameter is MAXSPRINTF.


**See Also :**
[MailFindNextHopToDomainExt](/reference/Func/MailFindNextHopToDomainExt)
[MailReloadRoutingTables](/reference/Func/MailReloadRoutingTables)
[MailUnloadRoutingTables](/reference/Func/MailUnloadRoutingTables)
[NEXTHOP_xxx (Output)](/reference/Symb/NEXTHOP_xxx (Output))
---
