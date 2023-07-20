##### Symbolic Value : Limits
##### MAXONESEGSIZE - Maximum single-segment memory object size.
---
```
#include <osmem.h>
```

**Symbolic Values :**



**Description :**

Defined for OSMem for those platforms with segmentation, allotting space for overhead. <br>
<br>
 Note: Beginning in V3.2, MAXONESEGSIZE is defined to be the MINIMUM of the required MAXONESEGSIZE on all platforms, because, for example, if a server allocates an object that is MAXONESEGSIZE and then sends it to a client, the client's definition of MAXONESEGSIZE must be the same as the server's.


**See Also :**
[OSMemAlloc](/domino-c-api-docs/reference/Func/OSMemAlloc)
[OSMemRealloc](/domino-c-api-docs/reference/Func/OSMemRealloc)
---
