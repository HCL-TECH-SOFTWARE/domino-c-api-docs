##### Data Type : Full Text Search
##### FT_SEARCH_RESULTS - Search results returned from FTSearch or FTSearchExt.
---
```
#include <ft.h>
```

**Definition :**
```
typedef struct {
   DWORD NumHits;   /* Number of search hits following */
   WORD  Flags;     /* see FT_RESULTS_xxx */
   WORD  VarLength; /* Length of variable strings after
                       FT_SEARCH_RESULT_ENTRY array, or
                       FT_SEARCH_URL_RESULT_ENTRY entries */

/* Followed by an array of 
       NoteIDs, 
       FT_SEARCH_RESULT_ENTRY's, OR
       FT_SEARCH_URL_RESULTS and FT_SEARCH_URL_RESULT_ENTRY's */

/* Followed by a BYTE array of scores (optional)
   OR in the case of catalog index search (searches done on a search 
   site database that has a multi-database index), the following are the
   Server, Title, Categories, Heading and Summary string fields */

} FT_SEARCH_RESULTS;
```

**Description :**

This structure contains the results of a full text search that is returned from FTSearch or FTSearchExt.
<ul><br>
<br>
If the Flags member of this structure has the FT_RESULTS_EXPANDED bit set, then an array of FT_SEARCH_RESULT_ENTRY structures will follow the FT_SEARCH_RESULTS structure.<br>
<br>
If the Flags memer of this structure has the FT_RESULTS_URL bit set, then the returned results consist of one FT_SEARCH_RESULTS structure, one FT_SEARCH_URL_RESULTS structure and an array of FT_SEARCH_URL_RESULT_ENTRY structures.  This is only supported by the FTSearchExt API.<br>
<br>
If the Flags member of this strucuture has the  FT_RESULTS_SCORES bit set, then an array of bytes containing the relevancy scores will follow the array of NoteIDs and be parallel to it.  Relevancy scores range from 0 to 100, with 100 being the most relevant.  Otherwise, relevancy scores are not returned.</ul>



**See Also :**
[FTSearch](/domino-c-api-docs/reference/Func/FTSearch)
[FTSearchExt](/domino-c-api-docs/reference/Func/FTSearchExt)
[FT_RESULTS_xxx](/domino-c-api-docs/reference/Symb/FT_RESULTS_xxx)
[FT_SEARCH_RESULT_ENTRY](/domino-c-api-docs/reference/Data/FT_SEARCH_RESULT_ENTRY)
[FT_SEARCH_URL_RESULTS](/domino-c-api-docs/reference/Data/FT_SEARCH_URL_RESULTS)
[FT_SEARCH_URL_RESULT_ENTRY](/domino-c-api-docs/reference/Data/FT_SEARCH_URL_RESULT_ENTRY)
---
