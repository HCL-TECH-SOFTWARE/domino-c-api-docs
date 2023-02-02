##### Data Type : Full Text Search
##### FT_SEARCH_RESULT_ENTRY - Search results that may be returned from FTSearch.
---
##### #include <ft.h>
**Description :**
FTSearch returns an FT_SEARCH_RESULTS structure.  If the Flags member of the 
FT_SEARCH_RESULTS structure has the FT_RESULTS_EXPANDED bit set, then an array 
of FT_SEARCH_RESULT_ENTRY structures will follow the FT_SEARCH_RESULTS 
structure.  This will occur with searches done on a search site database that 
has a multi-database index.

The Server, Title, Categories, Heading and Summary string fields follow the 
FT_SEARCH_RESULT_ENTRY array.
   
**See Also :**
[FTSearch](D:/md_files/FTSearch.md)
[FT_SEARCH_RESULTS](D:/md_files/FT_SEARCH_RESULTS.md)
[FT_RESULTS_xxx](D:/md_files/FT_RESULTS_xxx.md)
---
