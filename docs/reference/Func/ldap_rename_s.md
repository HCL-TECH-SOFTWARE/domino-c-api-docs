##### Function : LDAP
##### ldap_rename_s - Initiate a synchronous ldap modify DN operation.
---
```
#include <ldap.h>
int LNPUBLIC ldap_rename_s(

	LDAP *ld,
	const char *dn,
	const char *newrdn,
	const char *newparent,
	int  deleteoldrdn,
	LDAPControl **serverctrls,
	LDAPControl **clientctrls);
```
**Description :**

This function initiates a synchronous modify DN operation with controls.

Implemented as a macro:

#define ldap_rename_s(ld, dn, newrdn, newparent, deleteoldrdn, serverctrls, 
clientctrls) \
         ND_ldap_rename_s((ld), (dn), (newrdn), (newparent), (deleteoldrdn), 
(serverctrls), (clientctrls))

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The name of the entry whose distinguished name is to be changed.  If NULL, a zero length DN is sent to the server.

newrdn  -  The new RDN to give the entry.

newparent  -  The new parent, or superior entry.  If this parameter is NULL, only the RDN of the entry is changed.  The root DN SHOULD be specified by passing a zero length string, "".  The newparent parameter SHOULD always be NULL when using version 2 of the LDAP protocol; otherwise the server's behavior is undefined.

deleteoldrdn  -  This parameter only has meaning if newrdn is different than the old RDN. Boolean value: non-zero indicates that the old RDN value(s) is to be removed, zero indicates that the old RDN value(s) is to be retained as non-distinguished values of the entry.

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.



**Sample Usage :**
```
ldap_rename_s(ld, dn, newrdn, newparent, deleteoldrdn, serverctrls. 
clientctrls);
```
**See Also :**
---
