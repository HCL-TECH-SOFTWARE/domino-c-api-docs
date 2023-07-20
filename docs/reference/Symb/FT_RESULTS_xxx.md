##### Symbolic Value : Full Text Search
##### FT_RESULTS_xxx - FT_SEARCH_RESULTS Flags.
---
```
#include <ft.h>
```

**Symbolic Values :**

	FT_RESULTS_SCORES	  -  A parallel array of bytes containing the relevancy scores follow the array of NoteIDs in the FT_SEARCH_RESULTS structure.

	FT_RESULTS_EXPANDED	  -  Search results are series of FT_SEARCH_RESULT_ENTRY structures.

	FT_RESULTS_URL	  -  Search results are in the URL expanded format. 
Search results are returned in one FT_SEARCH_URL_RESULTS and series of FT_SEARCH_URL_RESULT_ENTRY structures. This is supported by FTSearchExt only


**Description :**

These values describe any additional data that may follow the FT_SEARCH_RESULTS structure that is returned by FTSearch or FTSearchExt.


**See Also :**
[FT_SEARCH_RESULTS](/domino-c-api-docs/reference/Data/FT_SEARCH_RESULTS)
[FTSearch](/domino-c-api-docs/reference/Func/FTSearch)
---
