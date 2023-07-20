##### Data Type : Views
##### COLLECTIONSTATS16 - Returned by NIFReadEntries.
---
```
#include <nif.h>
```

**Definition :**
```
typedef struct {
   WORD TopLevelEntries; /* # top level entries (level 0) */
   WORD spare[3];        /* 0 */
} COLLECTIONSTATS16;
```

**Description :**

If requested, this structure is returned by NIFReadEntries at the front of the returned information buffer.  The structure describes statistics about the overall collection.


**See Also :**
[NIFOpenCollection](/domino-c-api-docs/reference/Func/NIFOpenCollection)
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
[OPEN_xxx (collection)](/domino-c-api-docs/reference/Symb/OPEN_xxx (collection))
---
