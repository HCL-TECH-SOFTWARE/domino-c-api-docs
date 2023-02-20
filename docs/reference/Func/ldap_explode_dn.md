##### Function : LDAP
##### ldap_explode_dn - Break up a distinguished name into its component parts.
---
```
#include <ldap.h>
char **LNPUBLIC ldap_explode_dn(

	const char *dn,
	int  notypes);
```
**Description :**

This function is used to break up a distinguished name into its component parts.

Implemented as a macro:

#define ldap_explode_dn(dn, notypes) ND_ldap_explode_dn((dn), (notypes))

**Parameters :**
Input :
dn  -  The dn to explode, such as returned by ldap_get_dn.  If NULL, a zero length DN is used.

notypes  -  A boolean parameter.  If non-zero, the dn  components are to have their type information stripped off (i.e., "cn=Babs" would become "Babs").

Output :
(routine)  -  A NULL terminated char * array containing the RDN components of the DN supplied, with or without types as indicated by the notypes parameter. The components are returned in the order they appear in the dn.  The array returned SHOULD be freed when it is no longer in use by calling ldap_value_free.



**See Also :**
[ldap_get_dn](/reference/Func/ldap_get_dn)
[ldap_value_free](/reference/Func/ldap_value_free)
---
