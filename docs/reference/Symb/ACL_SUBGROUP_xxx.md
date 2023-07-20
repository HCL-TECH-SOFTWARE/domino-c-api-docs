##### Symbolic Value : Access Control List
##### ACL_SUBGROUP_xxx - Privilege name delimiters.
---
```
#include <acl.h>
```

**Symbolic Values :**

	ACL_SUBGROUP_LEFT_PAREN	  -  '[' - Opening delimiter for role names.

	ACL_SUBGROUP_RIGHT_PAREN	  -  ']' - Closing delimiter for role names.


**Description :**

Beginning with Release 3 of Notes, up to 75 named &quot;roles&quot; may be defined for access control lists.  A role is added to an access control list by setting the appropriate privilege bit in the ACL_PRIVILEGES structure.  Role names begin with a left square bracket and end with a right square bracket.


**See Also :**
[ACLGetPrivName](/domino-c-api-docs/reference/Func/ACLGetPrivName)
[ACLSetPrivName](/domino-c-api-docs/reference/Func/ACLSetPrivName)
[ACL_PRIVILEGES](/domino-c-api-docs/reference/Data/ACL_PRIVILEGES)
---
