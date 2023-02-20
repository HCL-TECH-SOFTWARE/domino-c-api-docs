##### Function : LDAP
##### ldap_modrdn2 - Initiate an asynchronous ldap modify RDN operation.
---
```
#include <ldap.h>
int LNPUBLIC ldap_modrdn2(

	LDAP *ld,
	const char *dn,
	const char *newrdn,
	int  deleteoldrdn);
```
**Description :**

This function initiates an asynchronous modify RDN operation.

Implemented as a macro:

#define ldap_modrdn2(ld, dn, newrdn, deleteoldrdn)  ND_ldap_modrdn2((ld), (dn), 
(newrdn), (deleteoldrdn))

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The name of the entry whose RDN is to be changed.  If NULL, a zero length DN is sent to the server.

newrdn  -  The new RDN to give the entry.

deleteoldrdn  -  Boolean value: non-zero indicates that the old RDN value(s) is to be removed, zero indicates that the old RDN value(s) is to be retained as non-distinguished values of the entry.

Output :
(routine)  -  Message ID - This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.

-1 - If an error occurs.



**See Also :**
---
