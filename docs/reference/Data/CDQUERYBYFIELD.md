##### Data Type : Agents
##### CDQUERYBYFIELD - Query by Field query CD record.
---
```
#include <queryods.h>
```
**Description :**

Field-level query information is stored in a CDQUERYBYFIELD record in fields of 
type TYPE_QUERY, usually the query field of an Agent.  The query field of an 
Agent is used to select documents to be operated on by the Agent.  This record 
consists of this data structure, followed by the field name and any value for 
the field query (in packed format).  The fields in this structure are:

Header   Defines this composite data item as a CDQUERYBYFIELD item.
dwFlags  Field query flags (see QUERYBYFIELD_FLAG_xxx).
wDataType  Type of field to search (see TYPE_xxx).
wOperator  Field query operation (see QUERYBYFIELD_OP_xxx).
Date1   First TIMEDATE value for comparison.
Date2   Second TIMEDATE value defining a range.
Number1  First ALIGNED_NUMBER value for comparison.
Number2  Second ALIGNED_NUMBER value defining a range.
wFieldNameLen Length of the field name.
wValueLen  Length of the value.

This structure is followed by a packed string containing the field name and any 
field value.

**See Also :**
[QUERYBYFIELD_FLAG_xxx](/domino-c-api-docs/reference/Symb/QUERYBYFIELD_FLAG_xxx)
[QUERYBYFIELD_OP_xxx](/domino-c-api-docs/reference/Symb/QUERYBYFIELD_OP_xxx)
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
---
