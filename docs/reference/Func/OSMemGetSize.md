##### Function : OS Memory
##### OSMemGetSize - Get the size of a Domino memory object.
---
```
#include <osmem.h>
STATUS LNPUBLIC OSMemGetSize(

	DHANDLE  Handle,
	DWORD far *retSize);
```
**Description :**

OsMemGetSize is used to get the size of an object in bytes.  This function may 
return a size larger than the object was originally allocated, in the event 
that the operating system rounded up the size to the nearest allocation 
boundary.

Calling this routine with a HANDLE that is invalid or out of range will result 
in a Notes PANIC Halt.

**Parameters :**
Input :
Handle  -  Handle for the object whose size is to be returned

Output :
(routine)  -  Completion status of the operation -- Always returns NOERROR.  There is no need to check the return value.


retSize  -  The address of a DWORD in which the object size in bytes will be returned.


**See Also :**
[OSMemAlloc](/domino-c-api-docs/reference/Func/OSMemAlloc)
[OSMemRealloc](/domino-c-api-docs/reference/Func/OSMemRealloc)
[OSMemFree](/domino-c-api-docs/reference/Func/OSMemFree)
---
