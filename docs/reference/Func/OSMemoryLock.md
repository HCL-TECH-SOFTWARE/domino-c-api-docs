##### Function : OS Memory
##### OSMemoryLock - Lock an object in memory and return its address
---
```
#include <osmem.h>
void far * LNPUBLIC OSMemoryLock(

	MEMHANDLE  handle);
```
**Description :**

This function must be called before any memory object is referenced.  It takes 
the MEMHANDLE returned from the OSMemoryAllocate function, locks the object 
into memory to prevent swapping, and returns an address of the actual memory.  
If the object has been disarded, this function returns NULL.  This function can 
be called more than once for the same object because a lock count is 
maintained. 

**Parameters :**
Input :
handle  -  The MEMHANDLE returns from the OSMemoryAllocate function.

Output :
(routine)  -  None.



**See Also :**
[MEMHANDLE](/reference/Data/MEMHANDLE)
[OSMemoryAllocate](/reference/Func/OSMemoryAllocate)
[OSMemoryFree](/reference/Func/OSMemoryFree)
[OSMemoryGetSize](/reference/Func/OSMemoryGetSize)
[OSMemoryReallocate](/reference/Func/OSMemoryReallocate)
[OSMemoryUnlock](/reference/Func/OSMemoryUnlock)
---
