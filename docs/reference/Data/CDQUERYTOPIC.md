##### Data Type : Agents
##### CDQUERYTOPIC - Verity Topic query CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG Header;
   DWORD dwFlags;       /* Flags */
   WORD wTopicQueryLen; /* Length of topic query */
   WORD wDataLen;       /* Length of data */
  /* Topic query follows */
  /* Data follows */
 } CDQUERYTOPIC;

**Description :**

Domino and Notes incorporate a search engine provided by Verity, Inc.  Search queries for the Verity search engine are stored in CDQUERYTOPIC records in fields of type TYPE_QUERY, usually the query field of an Agent.  The query is used by the Verity search engine to select the documents to be operated on by the Agent.  This record consists of this data structure followed by the query topic and data for the search.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDQUERYTOPIC item.<br>
dwFlags		Reserved;  must be 0.<br>
wTopicQueryLen	Length of query topic.<br>
wDataLen		Length of query data.</ul>
<br>
This structure is followed by the query topic, then the query data.</ul>



**See Also :**
---
