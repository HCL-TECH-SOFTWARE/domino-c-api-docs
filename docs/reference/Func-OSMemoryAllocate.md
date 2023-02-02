##### Function : OS Memory
##### OSMemoryAllocate - Allocate a block of memory - returns MEMHANDLE
---
##### #include <osmem.h>
STATUS LNPUBLIC **OSMemoryAllocate(**

	DWORD  dwtype,
	DWORD  size,
	MEMHANDLE *rethandle);
**Description :**
 It is advisable to use the OSMemoryAllocate function, instead of the 
OSMemAlloc function, at the places where Domino or Notes takes a pointer to the 
data, and you choose to use the Domino memory allocator to allocate storage for 
that data. 

       This function returns MEMHANDLE which has no relationship with the 
datatype HANDLE.  A HANDLE is a WORD on all platforms except Win32.  On Win32, 
it is a DWORD, but the HANDLE is still restricted to 16 bits of actual usage, 
which limits an application to 64K HANDLEs.  Due to a Domino algorithm change, 
OSMemoryAllocate returns DWORD MEMHANDLEs which free the constraint posed by 
the size of the HANDLE datatype. 

        OSMemoryAllocate allocates a block of memory and returns a MEMHANDLE 
handle to the caller.  The memory should be locked with the function 
OSMemoryLock, and unlocked and released using the function OSMemoryUnlock and 
OSMemoryFree respectively.

        This function guarantees that if the memory allocation fails, the 
returned handle will be NULLMEMHANDLE.  Unlike OSMemAlloc, this function 
allocates 0 byte if that is requested, instead of returning a NULLHANDLE with 
success.

**Parameters :**
Input :
dwtype  -  Type of memory block to be allocated.  Use 0 to allocate a block of memory for the application's use.  To allocate memory that can be shared between processes, use MEM_SHARE.  For allocated memory that may be reallocated to a different size, use MEM_GROWABLE.  See Symbolic Value, MEM_xxx for more information.

size  -  Size needed in bytes.  The maximum size is MAXONESEGSIZE.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


rethandle  -  MEMHANDLE to newly allocated object

**See Also :**
[MEMHANDLE](D:/md_files/MEMHANDLE.md)
[MEM_xxx](D:/md_files/MEM_xxx.md)
[OSMemAlloc](D:/md_files/OSMemAlloc.md)
[OSMemoryFree](D:/md_files/OSMemoryFree.md)
[OSMemoryGetSize](D:/md_files/OSMemoryGetSize.md)
[OSMemoryLock](D:/md_files/OSMemoryLock.md)
[OSMemoryReallocate](D:/md_files/OSMemoryReallocate.md)
[OSMemoryUnlock](D:/md_files/OSMemoryUnlock.md)
[OSMemRealloc](D:/md_files/OSMemRealloc.md)
---
