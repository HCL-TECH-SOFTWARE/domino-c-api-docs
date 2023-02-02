##### Function : OS Memory
##### OSMemoryGetSize - Get size of an MEMHANDLE object
---
##### #include <osmem.h>
DWORD LNPUBLIC **OSMemoryGetSize(**

	MEMHANDLE  handle);
**Description :**
This function can be used to obtain the size of an object in bytes.  It returns 
the amount of space actually available, not the size originally requested.
**Parameters :**
Input :
handle  -  Object handle

Output :
(routine)  -  The address of a DWORD in which the MEMHANDLE object size in bytes will be returned.


**See Also :**
[MEMHANDLE](D:/md_files/MEMHANDLE.md)
[OSMemoryAllocate](D:/md_files/OSMemoryAllocate.md)
[OSMemoryFree](D:/md_files/OSMemoryFree.md)
[OSMemoryLock](D:/md_files/OSMemoryLock.md)
[OSMemoryReallocate](D:/md_files/OSMemoryReallocate.md)
[OSMemoryUnlock](D:/md_files/OSMemoryUnlock.md)
---
