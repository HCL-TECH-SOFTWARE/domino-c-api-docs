##### Function : Mail Gateway
##### MailLookupAddress - Returns the full mail address of the specified user.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailLookupAddress(

	char far *UserName,
	char far *MailAddress);
```
**Description :**

This function returns the full mail address of the specified user.  This 
function is typically used by gateways to translate an inbound recipient name 
to his or her Domino mail address.  The mail address consists of the user name 
and the domain name,  for example:  "John Smith @ Iris".  If the user has a 
Forwarding Address specified, the forwarding address will be returned instead.

This function looks in the local copy of the Domino Directory (Server's Address 
book) and does not look to the mail server for this information.  This function 
is designed to be used in mail gateway programs that run on a Lotus Domino 
Server replicating the Domino Directory, rather than on a Notes workstation 
machine.

**Parameters :**
Input :
UserName  -  User name string pointer (null-terminated).  The UserName string can be any one of the following:  FullName, FirstName, LastName, ShortName.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR), specified username not found in the Domino Directory. (ERR_ROUTER_NOSUCHUSER), or specified username has more than one match in the Domino Directory (ERR_ROUTER_NOTUNIQUE).


MailAddress  -  Mail address string (null-terminated) up to MAXRECIPIENTNAME+1 in length (includes null terminator).


**See Also :**
[MailLookupUser](/domino-c-api-docs/reference/Func/MailLookupUser)
[MailAddRecipientsItem](/domino-c-api-docs/reference/Func/MailAddRecipientsItem)
---
