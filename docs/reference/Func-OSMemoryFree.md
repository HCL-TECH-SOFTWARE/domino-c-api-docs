##### Function : OS Memory
##### OSMemoryFree - Deallocate memory
---
##### #include <osmem.h>
void LNPUBLIC **OSMemoryFree(**

	MEMHANDLE  handle);
**Description :**
OSMemoryFree is used to deallocate a block  or memory using the handle 
MEMHANDLE returned from OSMemoryAllocate.
**Parameters :**
Input :
handle  -  Object handle returned by the OSMemoryAllocate function.  If the handle is NULLMEMHANDLE, no error will be reported.


**See Also :**
[MEMHANDLE](D:/md_files/MEMHANDLE.md)
[OSMemoryAllocate](D:/md_files/OSMemoryAllocate.md)
[OSMemoryGetSize](D:/md_files/OSMemoryGetSize.md)
[OSMemoryLock](D:/md_files/OSMemoryLock.md)
[OSMemoryReallocate](D:/md_files/OSMemoryReallocate.md)
[OSMemoryUnlock](D:/md_files/OSMemoryUnlock.md)
[OSMemRealloc](D:/md_files/OSMemRealloc.md)
---
