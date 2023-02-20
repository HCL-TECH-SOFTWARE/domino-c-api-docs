##### Function : LDAP
##### ldap_modrdn_s - Initiate a synchronous ldap modify RDN operation.
---
```
#include <ldap.h>
int LNPUBLIC ldap_modrdn_s(

	LDAP *ld,
	const char *dn,
	const char *newrdn);
```
**Description :**

This function will initiate a synchronous ldap modify RDN operation.

Implemented as a macro:

#define ldap_modrdn_s(ld, dn, newrdn) ND_ldap_modrdn_s((ld), (dn), (newrdn))

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The name of the entry whose RDN is to be changed.  If NULL, a zero length DN is sent to the server.

newrdn  -  The new RDN to give the entry.

Output :
(routine)  -   LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.



**See Also :**
---
