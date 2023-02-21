##### Function : Access Control List
##### ACLClearPriv - Clear a bit in an ACL_PRIVILEGES structure.
---
```
#include <acl.h>
void ACLClearPriv(

	ACL_PRIVILEGES  Priv,
	WORD  Num);
```
**Description :**

This is a macro that clears the given bit in an ACL_PRIVILEGES structure.

**Parameters :**
Input :
Priv  -  Privilege bit mask.  The privilege bit mask is a structure where each bit represents a role that may be set for each entry in an access control list.  The first five bits (bit number 0 through 4) are reserved for the five "privilege levels", used in versions of Notes before Release 3.   Each of the other bits maps to a role name.  Roles are assigned to an access control list entry by setting the appropriate bits in the privilege bit mask.

Num  -  The bit number (0 through ACL_PRIVCOUNT - 1) of the bit to be cleared.

Output :
(routine)  -  none


Priv  -  The resulting privilege bit mask with the desired bit cleared.


**See Also :**
[ACLSetPriv](/domino-c-api-docs/reference/Func/ACLSetPriv)
[ACL_PRIVILEGES](/domino-c-api-docs/reference/Data/ACL_PRIVILEGES)
[ACLInvertPriv](/domino-c-api-docs/reference/Func/ACLInvertPriv)
[ACLIsPrivSet](/domino-c-api-docs/reference/Func/ACLIsPrivSet)
---
