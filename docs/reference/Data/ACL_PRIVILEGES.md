##### Data Type : Access Control List
##### ACL_PRIVILEGES - Privilege bit array.
---
```
#include <acl.h>
```
**Description :**

This structure is the privilege bit mask which is an array of bytes (totaling 
ACL_PRIVCOUNT number of bits).  Each bit represents a role.  The first five 
bits (bit number 0 through 4) are reserved for the five "privilege levels", 
used in versions of Notes before Release 3.  Each of the other bits maps to a 
role name.  Roles are assigned to an access control list entry by setting the 
appropriate bits in the prviliege bit mask.

**See Also :**
[ACLAddEntry](/reference/Func/ACLAddEntry)
[ACLClearPriv](/reference/Func/ACLClearPriv)
[ACLEnumEntries](/reference/Func/ACLEnumEntries)
[ACLGetPrivName](/reference/Func/ACLGetPrivName)
[ACLInvertPriv](/reference/Func/ACLInvertPriv)
[ACLIsPrivSet](/reference/Func/ACLIsPrivSet)
[ACLLookupAccess](/reference/Func/ACLLookupAccess)
[ACLSetPriv](/reference/Func/ACLSetPriv)
[ACLSetPrivName](/reference/Func/ACLSetPrivName)
[ACLUpdateEntry](/reference/Func/ACLUpdateEntry)
[ACL_BITPRIVxxx](/reference/Symb/ACL_BITPRIVxxx)
[ACL_PRIVCOUNT](/reference/Symb/ACL_PRIVCOUNT)
---
