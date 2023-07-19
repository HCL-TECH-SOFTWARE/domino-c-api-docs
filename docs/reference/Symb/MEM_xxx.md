##### Symbolic Value : OS Memory
##### MEM_xxx - Type of memory block to be allocated in OSMemAlloc.
---
```
#include <globerr.h>
```

**Symbolic Values :**

	MEM_SHARE	  -  Allocated memory is to be shared between processes.

	MEM_GROWABLE	  -  This flag must be set when first allocating a resizeable buffer (a buffer whose size can be reallocated to a different size later). Despite its name, this flag must be set whether reallocation is used to increase OR decrease the buffer's size.


**Description :**

These flags are used by OSMemAlloc and OSMemoryAllocate to specify the type of block to be allocated.  0 may be specified if none of these types is applicable.


**See Also :**
[OSMemAlloc](/domino-c-api-docs/reference/Func/OSMemAlloc)
[OSMemoryAllocate](/domino-c-api-docs/reference/Func/OSMemoryAllocate)
[OSMemoryReallocate](/domino-c-api-docs/reference/Func/OSMemoryReallocate)
[OSMemRealloc](/domino-c-api-docs/reference/Func/OSMemRealloc)
---
