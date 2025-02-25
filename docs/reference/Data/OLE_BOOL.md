##### Data Type : Standard
##### OLE_BOOL - Boolean value used by OLE.
---
```
#include <global.h>
```

**Definition :**
```
#ifdef MAC
typedef unsigned long OLE_BOOL
#else
typedef BOOL          OLE_BOOL;
#endif
```

**Description :**

Boolean value used by OLE.  This value may be set to either TRUE or FALSE.  OLE uses a different datatype for a boolean value than BOOL, the datatype that Domino and Notes uses for a boolean value.


**See Also :**
[BOOL](/domino-c-api-docs/reference/Data/BOOL)
---
