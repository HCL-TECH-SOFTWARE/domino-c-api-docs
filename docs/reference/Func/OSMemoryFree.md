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
[MEMHANDLE](/reference/Data/MEMHANDLE)
[OSMemoryAllocate](/reference/Func/OSMemoryAllocate)
[OSMemoryGetSize](/reference/Func/OSMemoryGetSize)
[OSMemoryLock](/reference/Func/OSMemoryLock)
[OSMemoryReallocate](/reference/Func/OSMemoryReallocate)
[OSMemoryUnlock](/reference/Func/OSMemoryUnlock)
[OSMemRealloc](/reference/Func/OSMemRealloc)
---
