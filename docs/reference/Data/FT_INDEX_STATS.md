##### Data Type : Full Text Search
##### FT_INDEX_STATS - Statistics information returned from FTIndex.
---
```
#include <ft.h>
```

**Definition :**

typedef struct{
	DWORD  DocsAdded;  /* # of new documents */
	DWORD  DocsUpdated;  /* # of revised documents */
	DWORD  DocsDeleted;  /* # of deleted documents */
	DWORD  BytesIndexed;  /* # of bytes indexed */
	DWORD  Merges;   /* # of index merges */
	DWORD  MergeMsec;  /* Msec spent merging */
} FT_INDEX_STATS;

**Description :**

This structure contains statistics information that is returned when indexing a database for full text searching capabilities with FTIndex.


**See Also :**
[FTIndex](/domino-c-api-docs/reference/Func/FTIndex)
---
