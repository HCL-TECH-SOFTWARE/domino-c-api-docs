##### Data Type : IDs
##### DBLOCKID - Domino memory "block".
---
```
#include <pool.h>
```

**Definition :**
```
typedef struct {
   DHANDLE pool;  /* pool handle */
   DBLOCK block; /* block handle */
 } DBLOCKID;
```

**Description :**

This structure is used by Domino to manage a pool of memory which is subdivided into blocks of type DBLOCK.


**See Also :**
[DBLOCK](/domino-c-api-docs/reference/Data/DBLOCK)
---
