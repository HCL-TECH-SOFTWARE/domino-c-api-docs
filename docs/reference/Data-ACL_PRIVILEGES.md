##### Data Type : Access Control List
##### ACL_PRIVILEGES - Privilege bit array.
---
##### #include <acl.h>
**Description :**
This structure is the privilege bit mask which is an array of bytes (totaling 
ACL_PRIVCOUNT number of bits).  Each bit represents a role.  The first five 
bits (bit number 0 through 4) are reserved for the five "privilege levels", 
used in versions of Notes before Release 3.  Each of the other bits maps to a 
role name.  Roles are assigned to an access control list entry by setting the 
appropriate bits in the prviliege bit mask.
**See Also :**
[ACLAddEntry](D:/md_files/ACLAddEntry.md)
[ACLClearPriv](D:/md_files/ACLClearPriv.md)
[ACLEnumEntries](D:/md_files/ACLEnumEntries.md)
[ACLGetPrivName](D:/md_files/ACLGetPrivName.md)
[ACLInvertPriv](D:/md_files/ACLInvertPriv.md)
[ACLIsPrivSet](D:/md_files/ACLIsPrivSet.md)
[ACLLookupAccess](D:/md_files/ACLLookupAccess.md)
[ACLSetPriv](D:/md_files/ACLSetPriv.md)
[ACLSetPrivName](D:/md_files/ACLSetPrivName.md)
[ACLUpdateEntry](D:/md_files/ACLUpdateEntry.md)
[ACL_BITPRIVxxx](D:/md_files/ACL_BITPRIVxxx.md)
[ACL_PRIVCOUNT](D:/md_files/ACL_PRIVCOUNT.md)
---
