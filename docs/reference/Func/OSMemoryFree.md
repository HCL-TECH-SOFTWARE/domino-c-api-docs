##### Function : OS Memory
##### OSMemoryFree - Deallocate memory
---
```
#include <osmem.h>
void LNPUBLIC OSMemoryFree(

	MEMHANDLE  handle);
```
**Description :**

OSMemoryFree is used to deallocate a block  or memory using the handle 
MEMHANDLE returned from OSMemoryAllocate.

**Parameters :**
Input :
handle  -  Object handle returned by the OSMemoryAllocate function.  If the handle is NULLMEMHANDLE, no error will be reported.



**See Also :**
[MEMHANDLE](/domino-c-api-docs/reference/Data/MEMHANDLE)
[OSMemoryAllocate](/domino-c-api-docs/reference/Func/OSMemoryAllocate)
[OSMemoryGetSize](/domino-c-api-docs/reference/Func/OSMemoryGetSize)
[OSMemoryLock](/domino-c-api-docs/reference/Func/OSMemoryLock)
[OSMemoryReallocate](/domino-c-api-docs/reference/Func/OSMemoryReallocate)
[OSMemoryUnlock](/domino-c-api-docs/reference/Func/OSMemoryUnlock)
[OSMemRealloc](/domino-c-api-docs/reference/Func/OSMemRealloc)
---
