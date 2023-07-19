##### Data Type : Standard
##### QWORD - Unsigned 64-bit integer.
---
```
#include <global.h>
```

**Definition :**

#if (REQUIRED_ALIGNMENT == 8)
typedef double QWORD;
#else
typedef struct {DWORD Dwords[2];} QWORD;
#endif

**Description :**

A QWORD is an unsigned 64-bit integer.


**See Also :**
---
