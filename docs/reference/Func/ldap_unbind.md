##### Function : LDAP
##### ldap_unbind - Close all open connections associated with the LDAP session ID.
---
```
#include <ldap.h>
int LNPUBLIC ldap_unbind(

	LDAP *ld);
```
**Description :**

This function closes all open connections associated with the LDAP session ID, 
and disposes of all resources associated with the session handle before 
returning.

Implemented as a macro:

#define ldap_unbind(ld) ND_ldap_unbind((ld))

**Parameters :**
Input :
ld  -  The LDAP session handle.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.



**See Also :**
[ldap_bind](/reference/Func/ldap_bind)
[ldap_sasl_bind](/reference/Func/ldap_sasl_bind)
[ldap_simple_bind](/reference/Func/ldap_simple_bind)
[ldap_unbind_ext](/reference/Func/ldap_unbind_ext)
[ldap_unbind_s](/reference/Func/ldap_unbind_s)
---
