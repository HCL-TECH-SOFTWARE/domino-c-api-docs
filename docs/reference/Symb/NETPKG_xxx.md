##### Symbolic Value : Error Handling
##### NETPKG_xxx - Offsets within PKG_NETDRVLCL for local network drivers.
---
```
#include <globerr.h>
```

**Symbolic Values :**

	NETPKG_TCP	  -  TCP status code offset.

	NETPKG_ATALK	  -  ATALK status code offset

	NETPKG_NWSPX	  -  SPX status code offset.


**Description :**

These are the offsets within PKG_NETDRVLCL status codes used for local network drivers.  On Unix, since tcp is compiled into Domino, their strings must have unique IDs.  There is a separate package for all drivers which are optional and each optional driver package has its own offsets for first string.


**See Also :**
[PKG_xxx](/domino-c-api-docs/reference/Symb/PKG_xxx)
---
