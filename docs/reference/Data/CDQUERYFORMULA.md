##### Data Type : Agents
##### CDQUERYFORMULA - Formula query CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG Header;
   DWORD dwFlags;    /* flags */
   WORD wFormulaLen; /* Length of formula */
} CDQUERYFORMULA;

**Description :**

Formula queries are stored in CDQUERYFORMULA records in fields of type TYPE_QUERY, usually the query field of an Agent.  The formula is run to select the documents to be operated on by the Agent.  This record consists of this data structure followed by the formula.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDQUERYFORMULA item.<br>
dwFlags		Folder query flags (see QUERYFORMULA_FLAG_xxx).<br>
wFormulaLen		Length of the formula.</ul>
<br>
This structure is followed by the formula.</ul>



**See Also :**
[QUERYFORMULA_FLAG_xxx](/domino-c-api-docs/reference/Symb/QUERYFORMULA_FLAG_xxx)
---
