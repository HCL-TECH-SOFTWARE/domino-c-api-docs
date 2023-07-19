##### Data Type : Access Control List
##### ACL_PRIVILEGES - Privilege bit array.
---
```
#include <acl.h>
```

**Definition :**

typedef struct {BYTE BitMask[10]} ACL_PRIVILEGES;

**Description :**

This structure is the privilege bit mask which is an array of bytes (totaling ACL_PRIVCOUNT number of bits).  Each bit represents a role.  The first five bits (bit number 0 through 4) are reserved for the five &quot;privilege levels&quot;, used in versions of Notes before Release 3.  Each of the other bits maps to a role name.  Roles are assigned to an access control list entry by setting the appropriate bits in the prviliege bit mask.


**See Also :**
[ACLAddEntry](/domino-c-api-docs/reference/Func/ACLAddEntry)
[ACLClearPriv](/domino-c-api-docs/reference/Func/ACLClearPriv)
[ACLEnumEntries](/domino-c-api-docs/reference/Func/ACLEnumEntries)
[ACLGetPrivName](/domino-c-api-docs/reference/Func/ACLGetPrivName)
[ACLInvertPriv](/domino-c-api-docs/reference/Func/ACLInvertPriv)
[ACLIsPrivSet](/domino-c-api-docs/reference/Func/ACLIsPrivSet)
[ACLLookupAccess](/domino-c-api-docs/reference/Func/ACLLookupAccess)
[ACLSetPriv](/domino-c-api-docs/reference/Func/ACLSetPriv)
[ACLSetPrivName](/domino-c-api-docs/reference/Func/ACLSetPrivName)
[ACLUpdateEntry](/domino-c-api-docs/reference/Func/ACLUpdateEntry)
[ACL_BITPRIVxxx](/domino-c-api-docs/reference/Symb/ACL_BITPRIVxxx)
[ACL_PRIVCOUNT](/domino-c-api-docs/reference/Symb/ACL_PRIVCOUNT)
---
