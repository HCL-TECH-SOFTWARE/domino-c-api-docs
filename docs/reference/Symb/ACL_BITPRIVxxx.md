##### Symbolic Value : Access Control List
##### ACL_BITPRIVxxx - Release 2 access privileges.
---
```
#include <acl.h>
```

**Symbolic Values :**

	ACL_BITPRIVCOUNT	  -  Number of bits dedicated to Release 2 privileges.

	ACL_BITPRIVS	  -  Bit mask for Release 2 privileges.

	ACL_BITPRIV_LEFT_PAREN	  -  Opening delimiter for Release 2 privilege names.

	ACL_BITPRIV_RIGHT_PAREN	  -  Closing delimiter for Release 2 privilege names.


**Description :**

Originally, Notes supported 5 access privileges.  Beginning with Release 3 of Notes, those privileges are stored as 5 of the bits in the privileges bit array in an Access Control List.  Names of privileges are enclosed in parenthesis.


**See Also :**
[ACL_PRIVCOUNT](/domino-c-api-docs/reference/Symb/ACL_PRIVCOUNT)
[ACL_PRIVILEGES](/domino-c-api-docs/reference/Data/ACL_PRIVILEGES)
[ACL_PRIVNAMEMAX](/domino-c-api-docs/reference/Symb/ACL_PRIVNAMEMAX)
[ACL_PRIVSTRINGMAX](/domino-c-api-docs/reference/Symb/ACL_PRIVSTRINGMAX)
---
