##### Function : OS Memory
##### OSLockObject - Lock an object in memory and return its address.
---
```
#include <osmem.h>
void far * LNPUBLIC OSLockObject(

	DHANDLE  Handle);
```
**Description :**

OSLockObject locks a memory object (preventing its physical relocation) and 
returns a pointer to its locked address in memory.  This routine must be called 
before any memory object is referenced.  Once locked, the application can 
freely use the pointer to access its contents.

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
Handle  -  Handle for the object to be locked. 

Output :
(routine)  -  Pointer to the locked object.



**Sample Usage :**
```
  /* Get the physical address associated with the handle */

   pImpText = OSLockObject(ImpTextBID.pool);
   wCleanUp |= UNLOCK_IMPTEXTBID;

```
**See Also :**
[OSUnlockObject](/reference/Func/OSUnlockObject)
[OSMemAlloc](/reference/Func/OSMemAlloc)
[OSMemFree](/reference/Func/OSMemFree)
---
