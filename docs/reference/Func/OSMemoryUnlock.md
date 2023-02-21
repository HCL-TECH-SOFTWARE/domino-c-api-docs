##### Function : OS Memory
##### OSMemoryUnlock - Unlock a memory object
---
```
#include <osmem.h>
BOOL LNPUBLIC OSMemoryUnlock(

	MEMHANDLE  handle);
```
**Description :**

This function is used to unlock a memory object when it is no longer being 
referenced.  It decrements the lock count on the object, and, if no one else is 
using the object, makes it possible for the object to be moved or swapped.

This function returns TRUE if the object was previously locked, FALSE if not.

**Parameters :**
Input :
handle  -  The object handle.

Output :
(routine)  -  TRUE if the object was previously locked, FALSE if not.



**See Also :**
[MEMHANDLE](/domino-c-api-docs/reference/Data/MEMHANDLE)
[OSMemoryAllocate](/domino-c-api-docs/reference/Func/OSMemoryAllocate)
[OSMemoryFree](/domino-c-api-docs/reference/Func/OSMemoryFree)
[OSMemoryGetSize](/domino-c-api-docs/reference/Func/OSMemoryGetSize)
[OSMemoryLock](/domino-c-api-docs/reference/Func/OSMemoryLock)
[OSMemoryReallocate](/domino-c-api-docs/reference/Func/OSMemoryReallocate)
---
