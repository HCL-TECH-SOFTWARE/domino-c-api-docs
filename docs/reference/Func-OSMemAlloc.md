##### Function : OS Memory
##### OSMemAlloc - Allocate a block of memory from the Domino or Notes system.
---
##### #include <osmem.h>
STATUS LNPUBLIC **OSMemAlloc(**

	WORD  BlkType,
	DWORD  dwSize,
	DHANDLE far *retHandle);
**Description :**
OSMemAlloc allocates a block of memory and returns a handle to the caller.  The 
handle can be converted to a memory pointer by calling OSLockObject.

Under normal circumstances, memory allocated using OSMemAlloc must be released 
using the function OSMemFree.  (For the exceptions, please see the discussion 
under OSMemFree.)

This function is only necessary when allocating memory for which you need a 
handle to pass to C API functions.  If you need to allocate memory that does 
not require a handle, you can use the standard C function malloc() instead.
**Parameters :**
Input :
BlkType  -  Type of memory block to be allocated.  Use 0 to allocate a block of memory for the application's use.  To allocate memory that can be shared between processes, use MEM_SHARE.  For allocated memory that may be reallocated to a different size, use MEM_GROWABLE.  See Symbolic Value, MEM_xxx for more information.

dwSize  -  Requested size of memory block in bytes.  The limit is MAXDWORD.  If the requested size is 0 bytes, NULLHANDLE will be returned rather than a new handle.

Output :
(routine)  -  Error status code for allocate operation.  NOERROR if successful, or if not, one of the following:

ERR_MEMORY - Not enough global memory available for allocation.
ERR_SEGMENT_TOO_BIG - Requested size is greater than the maximum supported.


retHandle  -  The address of a HANDLE in which the handle to the allocated memory object is returned.  Guaranteed to be NULLHANDLE if allocate failed.  If the requested size is 0 bytes, NULLHANDLE will be returned rather than a new handle.

**Sample Usage :**
```
      /* Allocate a Domino or Notes memory object used in building an ITEM  */
      /* value                                                    */

       if (usError = OSMemAlloc(0, dwTextLen, &ImpTextBID.pool))
           goto Exit;
       else
           wCleanUp |= FREE_IMPTEXTBID;

```
**See Also :**
[MEM_xxx](D:/md_files/MEM_xxx.md)
[OSLockObject](D:/md_files/OSLockObject.md)
[OSMemFree](D:/md_files/OSMemFree.md)
[OSMemoryAllocate](D:/md_files/OSMemoryAllocate.md)
[OSMemoryReallocate](D:/md_files/OSMemoryReallocate.md)
[OSMemRealloc](D:/md_files/OSMemRealloc.md)
[OSUnlockObject](D:/md_files/OSUnlockObject.md)
---
