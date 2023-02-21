##### Function : LDAP
##### ldap_modify_ext - Asynchronously modify an existing LDAP entry with controls.
---
```
#include <ldap.h>
int LNPUBLIC ldap_modify_ext(

	LDAP *ld,
	const char *dn,
	LDAPMod **mods,
	LDAPControl **serverctrls,
	LDAPControl **clientctrls,
	int *msgid);
```
**Description :**

This function initiates an asynchronous modify operation with controls.

Implemented as a macro:

#define ldap_modify_ext(ld, dn, mods, serverctrls, clientctrls, msgid) \
	       ND_ldap_modify_ext((ld), (dn), (mods), (serverctrls), 
(clientctrls), (msgid))

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to modify.  If NULL, a zero length DN is sent to the server.

mods  -  List of modifications to make.  This is null-terminated array of struct ldapmod's, specifying the modifications to perform.

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

Output :
(routine)  -   LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


msgid  -  Pointer to the message id of the request if the ldap_modify_ext call succeeds. The value is undefined if a value other than LDAP_SUCCESS is returned.   This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.


**See Also :**
[LDAPMod](/domino-c-api-docs/reference/Data/LDAPMod)
[LDAP_OPT_xxx](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx)
---
