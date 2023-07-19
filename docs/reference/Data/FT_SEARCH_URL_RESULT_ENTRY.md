##### Data Type : Full Text Search
##### FT_SEARCH_URL_RESULT_ENTRY - Result entry returned by FTSearchExt when FT_RESULTS_URL set.
---
```
#include <ft.h>
```

**Definition :**

typedef struct {
   TIMEDATE CreatedTime;        /* Creation time of note */
   TIMEDATE ModifiedTime;       /* Last modified time of note */
   WORD     Flags;              /* Flags */
   WORD     UrlLength;          /* Length of url string, or 0 if
                                   notes link */
   DBID     ReplicaID;          /* replica id */
   UNID     Unid;               /* unid of note */
   UNID     ViewUnid;           /* unid of view containing note */
   WORD     ServerHintLength;   /* Length of Server hint */
   WORD     DbTitleLength;      /* Length of Database Title */
   WORD     DbCategoriesLength; /* Length of Database Categories */
   WORD     HeadingLength;      /* Length of View Column Heading */
   WORD     DocSummaryLength;   /* Length of Document Summary */
   WORD     DocTitleLength;     /* Length of Document Title */
   WORD     DocAuthorLength;    /* Length of Document Author */
   BYTE     Score;              /* Relevance score */
   BYTE     Spare;     
} FT_SEARCH_URL_RESULT_ENTRY;

**Description :**

FTSearchExt returns an FT_SEARCH_RESULTS structure.  If the Flags member of the<br>
FT_SEARCH_RESULTS structure has the FT_RESULTS_URL bit set, the following structures will<br>
be following:<br>

<ul>
<ul>one FT_SEARCH_URL_RESULTS structure,<br>
<br>
an array of FT_SEARCH_URL_RESULT_ENTRY structures <br>
<br>
an array of following variable length data (each set of variable data corresponds to each FT_SEARCH_URL_RESULT_ENTRY appeared above):
<ul>url string<br>
server hint string<br>
dbtitle string<br>
dbcategories strings<br>
heading string<br>
doc summary string<br>
doc title string<br>
doc author string</ul>
</ul>
</ul>
<br>

<ul>If there is a nonzero UrlLength, this is for a &quot;foreign&quot; url and the string should be used.  Otherwise the ReplicaID/Unid/ViewUnid/ServerHint represent the hit.</ul>



**See Also :**
---
