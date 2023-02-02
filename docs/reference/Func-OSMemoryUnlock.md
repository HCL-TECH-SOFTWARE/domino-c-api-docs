##### Function : OS Memory
##### OSMemoryUnlock - Unlock a memory object
---
##### #include <osmem.h>
BOOL LNPUBLIC **OSMemoryUnlock(**

	MEMHANDLE  handle);
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
[MEMHANDLE](D:/md_files/MEMHANDLE.md)
[OSMemoryAllocate](D:/md_files/OSMemoryAllocate.md)
[OSMemoryFree](D:/md_files/OSMemoryFree.md)
[OSMemoryGetSize](D:/md_files/OSMemoryGetSize.md)
[OSMemoryLock](D:/md_files/OSMemoryLock.md)
[OSMemoryReallocate](D:/md_files/OSMemoryReallocate.md)
---
