##### Function : OS Memory
##### OSUnlockObject - Unlock a Domino memory object.
---
##### #include <osmem.h>
BOOL LNPUBLIC **OSUnlockObject(**

	DHANDLE  Handle);
**Description :**
OSUnlockObject is called to indicate that an application no longer needs 
physical access to the specified object.  The lock count on the object is then 
decremented, and the calling application must then assume that the physical 
address for that object is no longer valid.  An object must be fully unlocked 
(reference count = 0) before it can be deallocated with OSMemFree.

It is recommended that once an application is temporarily done using a memory 
object, it unlock the object freeing up the memory for swapping to disk. 
OSLockObject can then be used for subsequent access, and the new pointer value 
must then be used for access.

An application can lock the same object more than once -- a lock reference 
count is maintained.  It is not actually moveable until all locks are released 
(reference count = 0).

Calling this routine with a HANDLE that is invalid or out of range will result 
in a Notes PANIC halt .
**Parameters :**
Input :
Handle  -  Handle for the  object to be unlocked.

Output :
(routine)  -   Always returns TRUE.  There is no need to check the return value.


**See Also :**
[OSLockObject](D:/md_files/OSLockObject.md)
[OSMemAlloc](D:/md_files/OSMemAlloc.md)
[OSMemFree](D:/md_files/OSMemFree.md)
[OSMemGetSize](D:/md_files/OSMemGetSize.md)
[OSUnlock](D:/md_files/OSUnlock.md)
[OSUnlockBlock](D:/md_files/OSUnlockBlock.md)
---
