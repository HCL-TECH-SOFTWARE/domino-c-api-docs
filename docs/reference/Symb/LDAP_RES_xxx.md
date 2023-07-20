##### Symbolic Value : LDAP
##### LDAP_RES_xxx - Possible result types a server can return.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_RES_BIND	  -  Result from a bind request.

	LDAP_RES_SEARCH_ENTRY	  -  A single entry matched a previously initiated search result.

	LDAP_RES_SEARCH_REFERENCE	  -  When the search result is a reference. (This was added in LDAP Version 3).

	LDAP_RES_SEARCH_RESULT	  -  Either a result indicating the final outcome of a previously initiated search operation or an entire chain of entries matching the search operation along with a final outcome.

	LDAP_RES_MODIFY	  -  Result from a modify request.

	LDAP_RES_ADD	  -  Result from an add request.

	LDAP_RES_DELETE	  -  Result from a delete request.

	LDAP_RES_MODRDN	  -  Result from a modify relative distiguished name request.

	LDAP_RES_MODDN	  -  Result from a modify distiguished name request.

	LDAP_RES_COMPARE	  -  Result from a compare request.

	LDAP_RES_EXTENDED	  -  Result from an extended request.

	LDAP_RES_ANY	  -  Any other result.


**Description :**

Possible result types a server can return.  Upon successful completion, ldap_result returns the type of the first result. This will be one of the following constants.


**See Also :**
[ldap_result](/domino-c-api-docs/reference/Func/ldap_result)
---
