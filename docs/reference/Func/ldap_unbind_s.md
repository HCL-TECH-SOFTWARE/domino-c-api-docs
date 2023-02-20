##### Function : LDAP
##### ldap_unbind_s - Close all open connections associated with the LDAP session ID.
---
```
#include <ldap.h>
int LNPUBLIC ldap_unbind_s(

	LDAP *ld);
```
**Description :**

This function closes all open connections associated with the LDAP session ID, 
and disposes of all resources associated with the session handle before 
returning.

Implemented as a macro:

#define ldap_unbind_s(ld) ND_ldap_unbind_s((ld)) 

**Parameters :**
Input :
ld  -  The LDAP session handle.

Output :
(routine)  -   LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.



**Sample Usage :**
```
ldap_unbind_s( ld );
```
**See Also :**
[ldap_bind_s](/reference/Func/ldap_bind_s)
[ldap_sasl_bind_s](/reference/Func/ldap_sasl_bind_s)
[ldap_simple_bind_s](/reference/Func/ldap_simple_bind_s)
[ldap_unbind](/reference/Func/ldap_unbind)
[ldap_unbind_ext](/reference/Func/ldap_unbind_ext)
---
