##### Function : OS Memory
##### OSMemoryGetSize - Get size of an MEMHANDLE object
---
```
#include <osmem.h>
DWORD LNPUBLIC OSMemoryGetSize(

	MEMHANDLE  handle);
```
**Description :**

This function can be used to obtain the size of an object in bytes.  It returns 
the amount of space actually available, not the size originally requested.

**Parameters :**
Input :
handle  -  Object handle

Output :
(routine)  -  The address of a DWORD in which the MEMHANDLE object size in bytes will be returned.



**See Also :**
[MEMHANDLE](/domino-c-api-docs/reference/Data/MEMHANDLE)
[OSMemoryAllocate](/domino-c-api-docs/reference/Func/OSMemoryAllocate)
[OSMemoryFree](/domino-c-api-docs/reference/Func/OSMemoryFree)
[OSMemoryLock](/domino-c-api-docs/reference/Func/OSMemoryLock)
[OSMemoryReallocate](/domino-c-api-docs/reference/Func/OSMemoryReallocate)
[OSMemoryUnlock](/domino-c-api-docs/reference/Func/OSMemoryUnlock)
---
