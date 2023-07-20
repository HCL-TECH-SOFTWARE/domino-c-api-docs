##### Data Type : Views
##### COLLECTIONPOSITION16 - COLLECTIONPOSITION structure used in Notes Release 3.
---
```
#include <nif.h>
```

**Definition :**
```
typedef struct {
   WORD Level;    /* # levels -1 in tumbler (top level = 0) */
   WORD Tumbler[MAXTUMBLERLEVELS_V2]; /* Current tumbler */
                 /* (1.2.3, etc) an array of ordinal ranks */
                 /* (0th entry = top level) */
 } COLLECTIONPOSITION16;
```

**Description :**

COLLECTIONPOSITION structure used in Notes Release 3.


**See Also :**
[COLLECTIONPOSITIONSIZE16](/domino-c-api-docs/reference/Func/COLLECTIONPOSITIONSIZE16)
---
