##### Data Type : Agents
##### CDQUERYHEADER - Query header CD record.
---
```
#include <queryods.h>
```
**Description :**

The on-disk format for a query consists of a query header structure followed by 
a number of query term structures.  The CDQUERYHEADER record is located at the 
beginning of a data item of TYPE_QUERY, usually the query field of an Agent.  
The fields in this structure are:

Header Defines this composite data item as a CDQUERYHEADER item.
dwFlags Query flags (see QUERY_FLAG_xxx).


**See Also :**
[QUERY_FLAG_xxx](/domino-c-api-docs/reference/Symb/QUERY_FLAG_xxx)
---
