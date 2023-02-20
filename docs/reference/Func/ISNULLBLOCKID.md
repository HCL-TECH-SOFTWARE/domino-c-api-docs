##### Function : OS Blocks
##### ISNULLBLOCKID - Test a BLOCKID for NULL.
---
```
#include <pool.h>
BOOL ISNULLBLOCKID(

	BLOCKID  x);
```
**Description :**

ISNULLBLOCKID is used to check a BLOCKID to see if it is NULL (empty).

This function is actually implemented as a macro:
#define ISNULLBLOCKID(x) (((x).pool==NULLHANDLE)&&((x).block==NULLBLOCK))

**Parameters :**
Input :
x  -  The BLOCKID to test for NULL

Output :
(routine)  -  TRUE if the specified BLOCKID is NULL, FALSE otherwise.



**See Also :**
[NSFItemAppendByBLOCKID](/reference/Func/NSFItemAppendByBLOCKID)
[NSFItemDeleteByBLOCKID](/reference/Func/NSFItemDeleteByBLOCKID)
[OSLockBlock](/reference/Func/OSLockBlock)
[OSUnlockBlock](/reference/Func/OSUnlockBlock)
---
