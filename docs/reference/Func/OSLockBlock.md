##### Function : OS Blocks
##### OSLockBlock - Locks BLOCKID and returns typed pointer to the data.
---
```
#include <pool.h>
<type> far * OSLockBlock(

	<typedef>  type,
	BLOCKID  blockid);
```
**Description :**

OSLockBlock locks the data associated with a BLOCKID in memory and returns a 
type cast pointer to its locked address in memory.  This routine must be called 
before any BLOCKID data can be referenced.  Once locked, the application can 
use the pointer to access the data.  The BLOCKID must be unlocked by the 
application using OSUnlockBlock before any corresponding Domino data entities 
(e.g. NSF, note, etc) can be freed (e.g. closed).

If the block of memory contains data that varies in size, such as a text list, 
the memory may be relocated unexpectedly.  To avoid this, the block should only 
be locked while accessing the contents, and should be unlocked immediately 
after.

Calling this routine with a BLOCKID that is invalid or out of range will result 
in a Notes PANIC halt!

Note -- this function is actually implemented as a macro:
 

#define OSLockBlock(type,blockid) \
 ((type far *)(OSLock(char,(blockid).pool) + (blockid).block))

**Parameters :**
Input :
type  -  The data type of the data associated with the given BLOCKID.

blockid  -  The BLOCKID to be locked.

Output :
(routine)  -  Pointer to a data item of the specified type.



**Sample Usage :**
```

       pTmpCD = OSLockBlock(char, bidTmpCD);
       CleanUp_State += UNLOCK_EXPCDBID;

```
**See Also :**
[ISNULLBLOCKID](/domino-c-api-docs/reference/Func/ISNULLBLOCKID)
[OSUnlockBlock](/domino-c-api-docs/reference/Func/OSUnlockBlock)
[OSLock](/domino-c-api-docs/reference/Func/OSLock)
[OSUnlock](/domino-c-api-docs/reference/Func/OSUnlock)
---
