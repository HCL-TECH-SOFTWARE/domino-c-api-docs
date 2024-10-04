##### Function : OS Memory
##### OSLock - Lock an object and return a type-cast pointer to it.
---
```
#include <osmem.h>
<blocktype> far * OSLock(

	<typedef>  blocktype,
	DHANDLE  handle);
```
**Description :**

OSLock locks a memory object and returns a pointer to its locked address in 
memory.  The pointer is type cast as given by the first argument.  This routine 
must be called before any memory object is referenced.  Once locked, the 
application can use the pointer to access its contents.

If the block of memory contains data that varies in size, such as a text list, 
the memory may be relocated unexpectedly.  To avoid this, the block should only 
be locked while accessing the contents, and should be unlocked immediately 
after.  It is recommended that once an application is temporarily done using a 
memory object, it unlock the object freeing up the memory for swapping to 
disk.  OSLock can then be used for subsequent access, and the new pointer value 
must then be used for access.

An application can lock the same object more than once -- a lock reference 
count is maintained.

Calling this routine with a DHANDLE that is invalid or out of range will result 
in a Notes PANIC halt .

Note: this routine is implemented as a macro around OSLockObject:


#define OSLock(blocktype,handle) ((blocktype far *) OSLockObject(handle))

**Parameters :**
Input :
blocktype  -  This argument should be a C language data type, either a native type or a TYPEDEFed one.  The returned pointer will be type-cast to point to data of this type.

hObject  -  Handle for the object to be locked. 

Output :
(routine)  -  Pointer to a data item of the specified type. 



**Sample Usage :**
```
  /* Obtain physical address of output ITEM value returned above. */

   pCDBuf = OSLock(char, hCDBuf);
   wCleanUp |= UNLOCK_HCDBUF;


```
**See Also :**
[OSLockBlock](/domino-c-api-docs/reference/Func/OSLockBlock)
[OSLockObject](/domino-c-api-docs/reference/Func/OSLockObject)
[OSUnlock](/domino-c-api-docs/reference/Func/OSUnlock)
[OSUnlockBlock](/domino-c-api-docs/reference/Func/OSUnlockBlock)
[OSUnlockObject](/domino-c-api-docs/reference/Func/OSUnlockObject)
---
