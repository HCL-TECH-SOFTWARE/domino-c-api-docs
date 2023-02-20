##### Function : OS Memory
##### OSMemoryReallocate - Change the allocated size of an object
---
```
#include <osmem.h>
STATUS LNPUBLIC OSMemoryReallocate(

	MEMHANDLE  handle,
	DWORD  size);
```
**Description :**

Use this function to increase or decrease the allocated size of a memory 
object.  If the size is increased, a new block may be allocated, but the old 
contents will be copied to the new block.  Reallocations are allowed while the 
block is locked, but the caller MUST refresh all pointers to the block since it 
is extremely likely that the block will have been moved after the reallocation.

Note - This function can resize only those buffers originally allocated using 
the MEM_GROWABLE flag.  See MEM_xxx for details.

**Parameters :**
Input :
handle  -  Handle to the memory object

size  -  New size in bytes

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[MEMHANDLE](/reference/Data/MEMHANDLE)
[MEM_xxx](/reference/Symb/MEM_xxx)
[OSMemAlloc](/reference/Func/OSMemAlloc)
[OSMemoryAllocate](/reference/Func/OSMemoryAllocate)
[OSMemoryFree](/reference/Func/OSMemoryFree)
[OSMemoryGetSize](/reference/Func/OSMemoryGetSize)
[OSMemoryLock](/reference/Func/OSMemoryLock)
[OSMemoryUnlock](/reference/Func/OSMemoryUnlock)
[OSMemRealloc](/reference/Func/OSMemRealloc)
---
