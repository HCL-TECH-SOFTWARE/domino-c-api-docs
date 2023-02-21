##### Function : LDAP
##### ldap_dn2ufn - Convert the distinguished name into a more "user friendly" format.
---
```
#include <ldap.h>
char *LNPUBLIC ldap_dn2ufn(

	const char *dn);
```
**Description :**

This function is used to convert the distinguished name into a more "user 
friendly" format.

Implemented as a macro:

#define ldap_dn2ufn(dn) ND_ldap_dn2ufn((dn)) 

**Parameters :**
Input :
dn  -  The dn to convert, such as returned by ldap_get_dn.

Output :
(routine)  -  A newly allocated space containing the name in "user friendly format" (UFN).  This space SHOULD be freed by a call to ldap_memfree when no longer in use.



**See Also :**
[ldap_get_dn](/domino-c-api-docs/reference/Func/ldap_get_dn)
[ldap_memfree](/domino-c-api-docs/reference/Func/ldap_memfree)
---
