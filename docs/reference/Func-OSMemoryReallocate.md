##### Function : OS Memory
##### OSMemoryReallocate - Change the allocated size of an object
---
##### #include <osmem.h>
STATUS LNPUBLIC **OSMemoryReallocate(**

	MEMHANDLE  handle,
	DWORD  size);
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
[MEMHANDLE](D:/md_files/MEMHANDLE.md)
[MEM_xxx](D:/md_files/MEM_xxx.md)
[OSMemAlloc](D:/md_files/OSMemAlloc.md)
[OSMemoryAllocate](D:/md_files/OSMemoryAllocate.md)
[OSMemoryFree](D:/md_files/OSMemoryFree.md)
[OSMemoryGetSize](D:/md_files/OSMemoryGetSize.md)
[OSMemoryLock](D:/md_files/OSMemoryLock.md)
[OSMemoryUnlock](D:/md_files/OSMemoryUnlock.md)
[OSMemRealloc](D:/md_files/OSMemRealloc.md)
---
