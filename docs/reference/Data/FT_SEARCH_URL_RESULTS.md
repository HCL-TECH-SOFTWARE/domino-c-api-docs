##### Data Type : Full Text Search
##### FT_SEARCH_URL_RESULTS - FTSearchExtSearch Results Header when FT_RESULTS_URL is set
---
```
#include <ft.h>
```

**Definition :**

typedef struct {
   DWORD HitCount;  /* Number of search hits (not necessarily
                       number returned) */
   WORD  VarLength; /* Length of variable length strings;
                       currently unused. */
} FT_SEARCH_URL_RESULTS;

**Description :**

Appears after FT_SEARCH_RESULTS when FT_RESULTS_URL is set and contains additional information from extended, multi-database searches.


**See Also :**
---
