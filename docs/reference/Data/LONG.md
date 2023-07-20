##### Data Type : Standard
##### LONG - Signed 32-bit integer.
---
```
#include <global.h>
```

**Definition :**
```
/* LONG - signed 32-bit integer */
#if !defined(OS2DEF_INCLUDED) && !defined(WINDOWS_INCLUDED)
   #if defined(LONGIS64BIT)
      typedef int LONG;
   #else
      typedef long LONG;
   #endif
#endif
```

**Description :**

A LONG is a signed 32-bit integer.


**See Also :**
[ULONG](/domino-c-api-docs/reference/Data/ULONG)
---
