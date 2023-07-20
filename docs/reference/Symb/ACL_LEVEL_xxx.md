##### Symbolic Value : Access Control List
##### ACL_LEVEL_xxx - Access Control Level symbols.
---
```
#include <acl.h>
```

**Symbolic Values :**

	ACL_LEVEL_NOACCESS	  -  User or Server has no access to the database.

	ACL_LEVEL_DEPOSITOR	  -  User or Server can add new data documents to a database, but cannot examine the new document or the database.

	ACL_LEVEL_READER	  -  User or Server can only view data documents in the database.

	ACL_LEVEL_AUTHOR	  -  User or Server can create and/or edit their own data documents and examine existing ones in the database.

	ACL_LEVEL_EDITOR	  -  User or Server can create and/or edit any data document.

	ACL_LEVEL_DESIGNER	  -  User or Server can create and/or edit any data document and/or design document.

	ACL_LEVEL_MANAGER	  -  User or Server can create and/or maintain any type of database or document, including the ACL.

	ACL_LEVEL_HIGHEST	  -  Highest access level.

	ACL_LEVEL_COUNT	  -  Number of access levels.


**Description :**

Access Control Level symbols used to qualify user or server access to a given Domino database.


**See Also :**
[SECKFMUserInfo](/domino-c-api-docs/reference/Func/SECKFMUserInfo)
[MAXUSERNAME](/domino-c-api-docs/reference/Symb/MAXUSERNAME)
[LICENSEID](/domino-c-api-docs/reference/Data/LICENSEID)
[ACLLookupAccess](/domino-c-api-docs/reference/Func/ACLLookupAccess)
[ACLAddEntry](/domino-c-api-docs/reference/Func/ACLAddEntry)
[ACLUpdateEntry](/domino-c-api-docs/reference/Func/ACLUpdateEntry)
[ACLEnumEntries](/domino-c-api-docs/reference/Func/ACLEnumEntries)
---
