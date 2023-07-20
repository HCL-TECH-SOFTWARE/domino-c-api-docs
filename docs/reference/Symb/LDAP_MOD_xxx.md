##### Symbolic Value : LDAP
##### LDAP_MOD_xxx - Determine which values to add, delete, or replace.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_MOD_ADD	  -  Values are added to the entry, creating the attribute if necessary.

	LDAP_MOD_DELETE	  -  Values are deleted from the entry, removing the attribute if no values remain. If the entire attribute is to be deleted, the mod_vals field can be set to NULL.

	LDAP_MOD_REPLACE	  -  Attribute will have the listed values after the modification, having been created if necessary, or removed if the mod_vals field is NULL. All modifications are performed in the order in which they are listed.

	LDAP_MOD_BVALUES	  -  BER values.


**Description :**

Determine which values to add, delete, or replace.


**See Also :**
[LDAPMod](/domino-c-api-docs/reference/Data/LDAPMod)
---
