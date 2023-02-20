##### Function : Access Control List
##### ACLInvertPriv - Inverts the given bit in an ACL_PRIVILEGES structure.
---
```
#include <acl.h>
void ACLInvertPriv(

	ACL_PRIVILEGES  Priv,
	WORD  Num);
```
**Description :**

This is a macro that inverts the given bit in an ACL_PRIVILEGES structure.  If 
the bit was originally set, it is cleared.  If the bit was originally cleared, 
it is set.

**Parameters :**
Input :
Priv  -  Privilege bit mask.  The privilege bit mask is a structure where each bit represents a role that may be set for each entry in an access control list.  The first five bits (bit number 0 through 4) are reserved for the five "privilege levels", used in versions of Notes before Release 3.   Each of the other bits maps to a role name.  Roles are assigned to an access control list entry by setting the appropriate bits in the privilege bit mask.

Num  -  The bit number (0 through ACL_PRIVCOUNT - 1) of the bit to be inverted.

Output :
(routine)  -  none


Priv  -  The resulting privilege bit mask with the desired bit inverted (cleared if originally set; set if originally cleared).


**See Also :**
[ACL_PRIVILEGES](/reference/Data/ACL_PRIVILEGES)
[ACLSetPriv](/reference/Func/ACLSetPriv)
[ACLClearPriv](/reference/Func/ACLClearPriv)
[ACLIsPrivSet](/reference/Func/ACLIsPrivSet)
---
