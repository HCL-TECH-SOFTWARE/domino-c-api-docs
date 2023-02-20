##### Function : LDAP
##### ldap_modrdn - Initiate an asynchronous ldap modify RDN operation.
---
```
#include <ldap.h>
int LNPUBLIC ldap_modrdn(

	LDAP *ld,
	const char *dn,
	const char *newrdn);
```
**Description :**

This function will initiate an asynchronous ldap modify RDN operation.

Implemented as a macro:

#define ldap_modrdn(ld, dn, newrdn) ND_ldap_modrdn((ld), (dn), (newrdn))

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The name of the entry whose RDN is to be changed.  If NULL, a zero length DN is sent to the server.

newrdn  -  The new RDN to give the entry.

Output :
(routine)  -  Message ID - This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.

-1 - If an error occurs.



**Sample Usage :**
```
msgid = ldap_modrdn( ld, dn, newrdn );
```
**See Also :**
---
