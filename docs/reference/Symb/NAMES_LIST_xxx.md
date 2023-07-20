##### Symbolic Value : Access Control List
##### NAMES_LIST_xxx - NAMES_LIST - Authentication flags.
---
```
#include <acl.h>
```

**Symbolic Values :**

	NAMES_LIST_AUTHENTICATED	  -  Set if names list has been authenticated via Notes.

	NAMES_LIST_PASSWORD_AUTHENTICATED	  -  Set if names list has been authenticated using external password -- Triggers "Maximum Internet name & password" (set in the database ACL) access level allowed.

	NAMES_LIST_FULL_ADMIN_ACCESS	  -  Set if user requested full admin access and it was granted.


**Description :**

Possible values for the Authenticated member of the NAMES_LIST structure.


**See Also :**
[NAMES_LIST](/domino-c-api-docs/reference/Data/NAMES_LIST)
[ACLLookupAccess](/domino-c-api-docs/reference/Func/ACLLookupAccess)
---
