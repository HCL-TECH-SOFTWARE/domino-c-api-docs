##### Symbolic Value : LDAP
##### LDAP_xxx_ATTRS - LDAP return attributes.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_ALL_OPERATIONAL_ATTRS	  -  All operational attributes are to be returned ("+"). This allows the request that all operational attributes in addition to any user attributes be returned.

	LDAP_ALL_USER_ATTRS	  -  All user attributes are to be returned ("*"). This allows the request that all user attributes in addition to any operational attributes be returned

	LDAP_NO_ATTRS	  -  No attribute types are to be returned by the server.


**Description :**

A list of attributes to be returned from each entry which matches the search filter.


**See Also :**
[ldap_search](/domino-c-api-docs/reference/Func/ldap_search)
[ldap_search_ext](/domino-c-api-docs/reference/Func/ldap_search_ext)
[ldap_search_ext_s](/domino-c-api-docs/reference/Func/ldap_search_ext_s)
[ldap_search_s](/domino-c-api-docs/reference/Func/ldap_search_s)
[ldap_search_st](/domino-c-api-docs/reference/Func/ldap_search_st)
---
