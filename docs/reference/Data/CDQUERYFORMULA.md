##### Data Type : Agents
##### CDQUERYFORMULA - Formula query CD record.
---
```
#include <queryods.h>
```
**Description :**

Formula queries are stored in CDQUERYFORMULA records in fields of type 
TYPE_QUERY, usually the query field of an Agent.  The formula is run to select 
the documents to be operated on by the Agent.  This record consists of this 
data structure followed by the formula.  The fields in this structure are:

Header  Defines this composite data item as a CDQUERYFORMULA item.
dwFlags  Folder query flags (see QUERYFORMULA_FLAG_xxx).
wFormulaLen  Length of the formula.

This structure is followed by the formula.

**See Also :**
[QUERYFORMULA_FLAG_xxx](/domino-c-api-docs/reference/Symb/QUERYFORMULA_FLAG_xxx)
---
