##### Function : LDAP
##### ldap_unbind_ext - Close all open connections associated with the LDAP session ID with client/server controls.
---
```
#include <ldap.h>
int LNPUBLIC ldap_unbind_ext(

	LDAP *ld,
	LDAPControl **serverctrls,
	LDAPControl **clientctrls);
```
**Description :**

Utilizing  client/server controls, this function closes all open connections 
associated with the LDAP session ID, and disposes of all resources associated 
with the session handle before returning.  

Note that since there is no server response to an unbind request, there is no 
way to receive a response to a server control sent with the unbind request. 

Implemented as a macro:

#define ldap_unbind_ext(ld, serverctrls, clientctrls) ND_ldap_unbind_ext((ld), 
(serverctrls), (clientctrls))

**Parameters :**
Input :
ld  -  The LDAP session handle.

serverctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

clientctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.



**See Also :**
[ldap_bind](/reference/Func/ldap_bind)
[ldap_bind_s](/reference/Func/ldap_bind_s)
[LDAP_OPT_xxx](/reference/Symb/LDAP_OPT_xxx)
[ldap_sasl_bind](/reference/Func/ldap_sasl_bind)
[ldap_sasl_bind_s](/reference/Func/ldap_sasl_bind_s)
[ldap_simple_bind](/reference/Func/ldap_simple_bind)
[ldap_simple_bind_s](/reference/Func/ldap_simple_bind_s)
[ldap_unbind](/reference/Func/ldap_unbind)
[ldap_unbind_s](/reference/Func/ldap_unbind_s)
---
