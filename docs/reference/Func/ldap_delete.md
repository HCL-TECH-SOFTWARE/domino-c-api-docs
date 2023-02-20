##### Function : LDAP
##### ldap_delete - Initiate an asynchronous ldap delete operation.
---
```
#include <ldap.h>
int LNPUBLIC ldap_delete(

	LDAP *ld,
	const char *dn);
```
**Description :**

This function will initiate an asynchronous ldap delete operation.

Note that the entry to delete must be a leaf entry (i.e., it must have no 
children). Deletion of entire subtrees in a single operation is not supported 
by LDAP.

Implemented as a macro:

#define ldap_delete(ld, dn) ND_ldap_delete((ld), (dn)) 

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to delete.  If NULL, a zero length DN is sent to the server.

Output :
(routine)  -  Message ID - This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.

-1 - If an error occurs.



**Sample Usage :**
```
msgid = ldap_delete( ld, dn );
```
**See Also :**
---
