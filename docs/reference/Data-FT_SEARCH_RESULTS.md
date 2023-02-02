##### Data Type : Full Text Search
##### FT_SEARCH_RESULTS - Search results returned from FTSearch or FTSearchExt.
---
##### #include <ft.h>
**Description :**
This structure contains the results of a full text search that is returned from 
FTSearch or FTSearchExt.

If the Flags member of this structure has the FT_RESULTS_EXPANDED bit set, then 
an array of FT_SEARCH_RESULT_ENTRY structures will follow the FT_SEARCH_RESULTS 
structure.

If the Flags memer of this structure has the FT_RESULTS_URL bit set, then the 
returned results consist of one FT_SEARCH_RESULTS structure, one 
FT_SEARCH_URL_RESULTS structure and an array of FT_SEARCH_URL_RESULT_ENTRY 
structures.  This is only supported by the FTSearchExt API.

If the Flags member of this strucuture has the  FT_RESULTS_SCORES bit set, then 
an array of bytes containing the relevancy scores will follow the array of 
NoteIDs and be parallel to it.  Relevancy scores range from 0 to 100, with 100 
being the most relevant.  Otherwise, relevancy scores are not returned.
**See Also :**
[FTSearch](D:/md_files/FTSearch.md)
[FTSearchExt](D:/md_files/FTSearchExt.md)
[FT_RESULTS_xxx](D:/md_files/FT_RESULTS_xxx.md)
[FT_SEARCH_RESULT_ENTRY](D:/md_files/FT_SEARCH_RESULT_ENTRY.md)
[FT_SEARCH_URL_RESULTS](D:/md_files/FT_SEARCH_URL_RESULTS.md)
[FT_SEARCH_URL_RESULT_ENTRY](D:/md_files/FT_SEARCH_URL_RESULT_ENTRY.md)
---
