##### Function : LDAP
##### ldap_delete_ext - Initiate an asynchronous ldap delete operation with controls.
---
```
#include <ldap.h>
int LNPUBLIC ldap_delete_ext(

	LDAP *ld,
	const char *dn,
	LDAPControl **serverctrls,
	LDAPControl **clientctrls,
	int *msgidp);
```
**Description :**

This function will initiate an asynchronous ldap delete operation with controls.

Note that the entry to delete must be a leaf entry (i.e., it must have no 
children). Deletion of entire subtrees in a single operation is not supported 
by LDAP.

Implemented as a macro:

#define ldap_delete_ext(ld, dn, sctrls, cctrls, msgidp)\
	        ND_ldap_delete_ext((ld), (dn), (sctrls), (cctrls), (msgidp)) 

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to delete.  If NULL, a zero length DN is sent to the server.

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


msgidp  -  Pointer to the message id of the request if the call succeeds. The value is undefined if a value other than LDAP_SUCCESS is returned.   This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.


**See Also :**
---
