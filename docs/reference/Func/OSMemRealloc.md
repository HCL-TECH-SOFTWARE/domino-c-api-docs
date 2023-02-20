##### Function : OS Memory
##### OSMemRealloc - Change the size of an existing Domino memory object.
---
```
#include <osmem.h>
STATUS LNPUBLIC OSMemRealloc(

	DHANDLE  Handle,
	DWORD  NewSize);
```
**Description :**

OSMemRealloc is used to increase or decrease the allocated size of a Domino 
memory object.  If the size is increased, then a new block may be allocated, 
but the block's contents will be copied to the new block. Reallocations are 
allowed while the block is locked, but the caller MUST refresh all pointers 
(using OSLockObject) to the block, since it is extremely likely that the block 
will have moved after the reallocation.

If you call this routine with a HANDLE that is invalid or out of range, Domino 
or Notes will panic and halt.

Note - This function can resize only those buffers originally allocated using 
the MEM_GROWABLE flag.  See MEM_xxx for details.

**Parameters :**
Input :
Handle  -  Handle for the memory object to be reallocated.

NewSize  -  The requested new size of the object, in bytes.

Output :
(routine)  -  Completion status of the operation, NOERROR if successful.  If not successful, then status is one of:

ERR_MEMORY - Not enough global memory available for allocation.

ERR_SEGMENT_TOO_BIG - Requested size is greater than the maximum supported (60K).



**See Also :**
[MEM_xxx](/reference/Symb/MEM_xxx)
[OSLockObject](/reference/Func/OSLockObject)
[OSMemAlloc](/reference/Func/OSMemAlloc)
[OSMemFree](/reference/Func/OSMemFree)
[OSMemGetSize](/reference/Func/OSMemGetSize)
[OSMemoryAllocate](/reference/Func/OSMemoryAllocate)
[OSMemoryReallocate](/reference/Func/OSMemoryReallocate)
[OSUnlockObject](/reference/Func/OSUnlockObject)
---
