##### Data Type : Full Text Search
##### FT_SEARCH_RESULT_ENTRY - Search results that may be returned from FTSearch.
---
```
#include <ft.h>
```

**Definition :**
```
typedef struct {
   DBID     ReplicaID;
   UNID     Unid;
   UNID     ViewUnid; 
   TIMEDATE ModifiedTime;     /* Last modified time of note */
   WORD     Flags;            /* see FT_RESULT_ENTRY_xxx */
   WORD     ServerHintLength; /* Length of Server hint */
   WORD     TitleLength;      /* Length of Databaes Title */
   WORD     CategoriesLength; /* Length of Database Categories */
   WORD     HeadingLength;    /* Length of View Column Heading */
   WORD     SummaryLength;    /* Length of View Summary */
   BYTE     Score;    
   BYTE     Spare;    
} FT_SEARCH_RESULT_ENTRY;
```

**Description :**

FTSearch returns an FT_SEARCH_RESULTS structure.  If the Flags member of the FT_SEARCH_RESULTS structure has the FT_RESULTS_EXPANDED bit set, then an array of FT_SEARCH_RESULT_ENTRY structures will follow the FT_SEARCH_RESULTS structure.  This will occur with searches done on a search site database that has a multi-database index.
<ul><br>
<br>
The Server, Title, Categories, Heading and Summary string fields follow the FT_SEARCH_RESULT_ENTRY array.<br>
   </ul>



**See Also :**
[FTSearch](/domino-c-api-docs/reference/Func/FTSearch)
[FT_SEARCH_RESULTS](/domino-c-api-docs/reference/Data/FT_SEARCH_RESULTS)
[FT_RESULTS_xxx](/domino-c-api-docs/reference/Symb/FT_RESULTS_xxx)
---
