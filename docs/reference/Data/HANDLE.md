##### Data Type : Handles
##### HANDLE - General definition for handles used by Domino and Notes.
---
```
#include <global.h>
```

**Definition :**

#if defined(DOSW16)
 typedef unsigned int HANDLE; /* really a short, but compiler is picky */
#elif defined(HANDLE_IS_32BITS)
 typedef unsigned int HANDLE; /* 32-bit HANDLEs */
#else
 typedef unsigned short HANDLE;
#endif


**Description :**

This datatype is the base type for various kinds of handles used by Domino and Notes.


**See Also :**
[OSMemAlloc](/domino-c-api-docs/reference/Func/OSMemAlloc)
[OSMemFree](/domino-c-api-docs/reference/Func/OSMemFree)
---
