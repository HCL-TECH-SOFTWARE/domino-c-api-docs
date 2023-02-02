##### Function : OS Blocks
##### OSUnlockBlock - Unlock a BLOCKID memory block.
---
##### #include <pool.h>
BOOL LNPUBLIC **OSUnlockBlock(**

	BLOCKID  blockid);
**Description :**
OSUnlockBlock is called to indicate that an application no longer needs 
physical access to the specified BLOCKID memory object. The lock count on the 
block is then decremented, and the calling application must then assume that 
the physical address for that object is no longer valid.  A BLOCKID must be 
fully unlocked (reference count = 0) before it can be deallocated.  Note that 
in the case of BLOCKIDs, operations such as closing Notes or databases require 
the corresponding BLOCKIDs to be fully unlocked.

Calling this routine with a BLOCKID that is invalid or out of range will result 
in a Notes PANIC halt .

Note -- this function is actually implemented as a macro:
#define OSUnlockBlock(blockid) \
 OSUnlockObject((blockid).pool)
**Parameters :**
Input :
blockid  -  BLOCKID for the block to be unlocked.

Output :
(routine)  -  Always returns TRUE.


**Sample Usage :**
```

       /* Unlock the CD Temp Buffer */
       if (CleanUp_State & UNLOCK_EXPCDBID)
           OSUnlockBlock(bidTmpCD);

```
**See Also :**
[OSLock](D:/md_files/OSLock.md)
[OSLockBlock](D:/md_files/OSLockBlock.md)
[OSLockObject](D:/md_files/OSLockObject.md)
[OSUnlock](D:/md_files/OSUnlock.md)
[OSUnlockObject](D:/md_files/OSUnlockObject.md)
---
