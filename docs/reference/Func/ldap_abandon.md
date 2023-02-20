##### Function : LDAP
##### ldap_abandon - Perform an LDAP abandon operation.
---
```
#include <ldap.h>
int LNPUBLIC ldap_abandon(

	LDAP *ld,
	int  msgid);
```
**Description :**

This function will perform an LDAP abandon of an operation in progress.

Implemented as a macro:

#define ldap_abandon(ld, msgid) ND_ldap_abandon((ld), (msgid))

**Parameters :**
Input :
ld  -  The LDAP session handle.

msgid  -  Message ID of the request to be abandoned.

Output :
(routine)  -  0 on success and -1 on error.



**See Also :**
---
