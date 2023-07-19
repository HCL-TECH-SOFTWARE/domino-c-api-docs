##### Data Type : Agents
##### CDQUERYUSESFORM - Query using form query CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG Header;
   DWORD dwFlags; /* Flags */
	 /* LIST structure follows */
} CDQUERYUSESFORM;

**Description :**

The names of the forms to be used in a query are stored in CDQUERYUSESFORM records in fields of type TYPE_QUERY, usually the query field of an Agent.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDQUERYUSESFORM item.<br>
dwFlags		Reserved;  must be 0.</ul>
<br>
This structure is followed by LIST structure containing the form names.</ul>



**See Also :**
[LIST](/domino-c-api-docs/reference/Data/LIST)
---
