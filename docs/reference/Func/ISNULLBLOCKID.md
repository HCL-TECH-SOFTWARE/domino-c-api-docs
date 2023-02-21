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
[NSFItemAppendByBLOCKID](/domino-c-api-docs/reference/Func/NSFItemAppendByBLOCKID)
[NSFItemDeleteByBLOCKID](/domino-c-api-docs/reference/Func/NSFItemDeleteByBLOCKID)
[OSLockBlock](/domino-c-api-docs/reference/Func/OSLockBlock)
[OSUnlockBlock](/domino-c-api-docs/reference/Func/OSUnlockBlock)
---
