##### Data Type : Agents
##### CDQUERYHEADER - Query header CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   BSIG Header;
   DWORD dwFlags; /* Flags for query */
} CDQUERYHEADER;

**Description :**

The on-disk format for a query consists of a query header structure followed by a number of query term structures.  The CDQUERYHEADER record is located at the beginning of a data item of TYPE_QUERY, usually the query field of an Agent.  The fields in this structure are:
<ul><br>

<ul>Header	Defines this composite data item as a CDQUERYHEADER item.<br>
dwFlags	Query flags (see QUERY_FLAG_xxx).</ul>
</ul>



**See Also :**
[QUERY_FLAG_xxx](/domino-c-api-docs/reference/Symb/QUERY_FLAG_xxx)
---
