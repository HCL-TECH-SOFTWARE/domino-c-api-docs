##### Data Type : Handles
##### BLOCK - A physical memory block within a BLOCKID.
---
```
#include <global.h>
```

**Definition :**

typedef WORD BLOCK;  /* pool block handle */

**Description :**

Type BLOCK is used to specify a particular memory block that is contained within a pool of blocks (BLOCKID structure).  API users should consider it a basic data entity from which the BLOCKID structure is built.  There is no need for API users to use a BLOCK data item directly; there are API macros provided that abstract the necessary operations to the BLOCKID level.


**See Also :**
[BLOCKID](/domino-c-api-docs/reference/Data/BLOCKID)
[NULLBLOCK](/domino-c-api-docs/reference/Symb/NULLBLOCK)
---
