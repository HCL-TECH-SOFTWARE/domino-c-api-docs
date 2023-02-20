##### Data Type : Full Text Search
##### FT_SEARCH_URL_RESULT_ENTRY - Result entry returned by FTSearchExt when FT_RESULTS_URL set.
---
```
#include <ft.h>
```
**Description :**

FTSearchExt returns an FT_SEARCH_RESULTS structure.  If the Flags member of the
FT_SEARCH_RESULTS structure has the FT_RESULTS_URL bit set, the following 
structures will
be following:

one FT_SEARCH_URL_RESULTS structure,

an array of FT_SEARCH_URL_RESULT_ENTRY structures 

an array of following variable length data (each set of variable data 
corresponds to each FT_SEARCH_URL_RESULT_ENTRY appeared above):
url string
server hint string
dbtitle string
dbcategories strings
heading string
doc summary string
doc title string
doc author string


If there is a nonzero UrlLength, this is for a "foreign" url and the string 
should be used.  Otherwise the ReplicaID/Unid/ViewUnid/ServerHint represent the 
hit.

**See Also :**
---
