##### Symbolic Value : Access Control List
##### ACL_UPDATE_xxx - ACLUpdateEntry flags.
---
```
#include <acl.h>
```

**Symbolic Values :**

	ACL_UPDATE_NAME	  -  The user's name is to be modified. The user entry is deleted and a new entry is created. Unless the other access control information is specified to be modified as well, the other access control information will be cleared and the user will have No Access to the database.

	ACL_UPDATE_LEVEL	  -  The user's access level is to be modified.

	ACL_UPDATE_PRIVILEGES	  -  The user's assigned privileges or roles are to be modified.

	ACL_UPDATE_FLAGS	  -  The user's access level modifier (eg: unable to delete documents) is to be modified.


**Description :**

Use these symbols when calling ACLUpdateEntry to specify what to modify in the access control list.  These values may be bitwise-OR'd together to modify multiple parameters.


**See Also :**
[ACLLookupAccess](/domino-c-api-docs/reference/Func/ACLLookupAccess)
[ACLAddEntry](/domino-c-api-docs/reference/Func/ACLAddEntry)
[ACLUpdateEntry](/domino-c-api-docs/reference/Func/ACLUpdateEntry)
[ACLEnumEntries](/domino-c-api-docs/reference/Func/ACLEnumEntries)
---
