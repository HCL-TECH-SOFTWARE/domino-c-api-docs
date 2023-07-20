##### Symbolic Value : LDAP
##### LDAP_SCOPE_xxx - Scopes for searching an LDAP directory.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_SCOPE_BASE	  -  A particular entry can be searched for.

	LDAP_SCOPE_ONELEVEL	  -  The search can be extended one level below the base, not including the base.

	LDAP_SCOPE_SUBTREE	  -  The whole subtree under the starting point can be searched.


**Description :**

Scopes for searching an LDAP directory.


**See Also :**
[ldap_search](/domino-c-api-docs/reference/Func/ldap_search)
[ldap_search_ext](/domino-c-api-docs/reference/Func/ldap_search_ext)
[ldap_search_ext_s](/domino-c-api-docs/reference/Func/ldap_search_ext_s)
[ldap_search_s](/domino-c-api-docs/reference/Func/ldap_search_s)
[ldap_search_st](/domino-c-api-docs/reference/Func/ldap_search_st)
---
