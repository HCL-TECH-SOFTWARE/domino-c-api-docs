##### Function : Access Control List
##### ACLIsPrivSet - Returns whether a given bit has been set in an ACL_PRIVILEGES structure.
---
##### #include <acl.h>
BOOL **ACLIsPrivSet(**

	ACL_PRIVILEGES  Priv,
	WORD  Num);
**Description :**
This is a macro that returns whether a given bit has been set in an 
ACL_PRIVILEGES structure.
**Parameters :**
Input :
Priv  -  Privilege bit mask.  The privilege bit mask is a structure where each bit represents a role that may be set for each entry in an access control list.  The first five bits (bit number 0 through 4) are reserved for the five "privilege levels", used in versions of Notes before Release 3.   Each of the other bits maps to a role name.  Roles are assigned to an access control list entry by setting the appropriate bits in the privilege bit mask.

Num  -  The bit number (0 through ACL_PRIVCOUNT - 1) of the bit in question.

Output :
(routine)  -  Non zero if the given bit is set, otherwise 0.


**See Also :**
[ACL_PRIVILEGES](D:/md_files/ACL_PRIVILEGES.md)
[ACLClearPriv](D:/md_files/ACLClearPriv.md)
[ACLSetPriv](D:/md_files/ACLSetPriv.md)
[ACLInvertPriv](D:/md_files/ACLInvertPriv.md)
---
