##### Symbolic Value : LDAP
##### mod_xxx - The values to add, delete, or replace.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	mod_values	  -  NULL terminated array of zero-terminated strings.

	mod_bvalues	  -  NULL terminated array of berval structures that can be used to pass binary values such as images.


**Description :**

The values to add, delete, or replace.  Only one of the mod_values or mod_bvalues variants can be used, selected by ORing the mod_op field (see LPADMod) with the constant LDAP_MOD_BVALUES (see LDAP_MOD_xxx).


**See Also :**
[LDAPMod](/domino-c-api-docs/reference/Data/LDAPMod)
[mod_vals_u_t](/domino-c-api-docs/reference/Data/mod_vals_u_t)
---
