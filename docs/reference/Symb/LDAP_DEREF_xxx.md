##### Symbolic Value : LDAP
##### LDAP_DEREF_xxx - Dereferencing aliases
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_DEREF_NEVER	  -  Aliases never dereferrenced.

	LDAP_DEREF_SEARCHING	  -  Aliases should be dereferenced during the search, but not when locating the base object of the search.

	LDAP_DEREF_FINDING	  -  Aliases should be dereferenced when locating the base object of the search, but not during the search.

	LDAP_DEREF_ALWAYS	  -  Aliases always dereferrenced.


**Description :**

Dereferencing aliases relating to LDAP_OPT_DEREF.  See LDAP_OPT_xxx.


**See Also :**
[LDAP_OPT_xxx](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx)
---
