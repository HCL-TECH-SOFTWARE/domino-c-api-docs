##### Symbolic Value : Access Control List
##### ACL_xxx - ACL-wide flags.  Get and set with ACLGetFlags and ACLSetFlags.
---
```
#include <acl.h>
```

**Symbolic Values :**

	ACL_UNIFORM_ACCESS	  -  Require same ACL in ALL replicas of database

	ACL_FLAG_ADMIN_READERAUTHOR	  -  Admin server can modify reader and author fields in database


**Description :**

These flags apply to the access control list itself.


**See Also :**
[ACLGetFlags](/domino-c-api-docs/reference/Func/ACLGetFlags)
[ACLSetFlags](/domino-c-api-docs/reference/Func/ACLSetFlags)
---
