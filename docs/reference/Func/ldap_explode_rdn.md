##### Function : LDAP
##### ldap_explode_rdn - Break up a relative distinguished name into its component parts.
---
```
#include <ldap.h>
char **LNPUBLIC ldap_explode_rdn(

	const char *rdn,
	int  notypes);
```
**Description :**

This function is used to break up a relative distinguished name into its 
component parts.

Implemented as a macro:

#define ldap_explode_rdn(rdn, notypes) ND_ldap_explode_rdn((rdn), (notypes))

**Parameters :**
Input :
rdn  -  The rdn to explode, such as returned in the components of the array returned by ldap_explode_dn.  If NULL, a zero length DN is used.

notypes  -  A boolean parameter.  If non-zero, the rdn  components are to have their type information stripped off (i.e., "cn=Babs" would become "Babs").

Output :
(routine)  -  A NULL terminated char * array containing the components of the RDN supplied, with or without types as indicated by the notypes parameter. The components are returned in the order they appear in the rdn.  The array returned SHOULD be freed when it is no longer in use by calling ldap_value_free.



**See Also :**
[ldap_explode_dn](/reference/Func/ldap_explode_dn)
[ldap_value_free](/reference/Func/ldap_value_free)
---
