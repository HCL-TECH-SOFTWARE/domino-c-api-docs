##### Function : Mail Gateway
##### MailGetDomainName - Returns the domain name of the local IBM Domino Server.
---
```
#include <mailserv.h>
STATUS LNPUBLIC MailGetDomainName(

	char far *Domain);
```
**Description :**

This function returns the domain name of the local IBM Domino Server.  The 
domain name is obtained from the DomainName field from the Server entry in the 
Domino Directory (Server's Address book).  The domain name is always returned 
in all upper case.

**Parameters :**

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


Domain  -  Domain name string (null-terminated).  


**See Also :**
[MailLookupAddress](/reference/Func/MailLookupAddress)
[MailLookupUser](/reference/Func/MailLookupUser)
---
