##### Symbolic Value : Distinguished Name
##### DN_xxx - Distinguished name flags.
---
```
#include <dname.h>
```

**Symbolic Values :**

	DN_NONSTANDARD	  -  Distinguished name includes non-standard components.

	DN_NONDISTINGUISHED	  -  Name is a non-distinguished name.

	DN_CN_OU_RDN	  -  Obsolete. CN plus OU components of the distinguished name are relative.

	DN_O_C_RDN	  -  Obsolete. O plus C components of the distinguished name are relative.

	DN_NONABBREV	  -  Name includes components that cannot be abbreviated.


**Description :**

These values are used in the DN_COMPONENTS structure to describe a distinguished name.  A value of 0L means that the distinguished name does not have any of the DN_xxx attributes.


**See Also :**
[DN_COMPONENTS](/domino-c-api-docs/reference/Data/DN_COMPONENTS)
---
