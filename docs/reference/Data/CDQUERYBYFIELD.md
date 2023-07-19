##### Data Type : Agents
##### CDQUERYBYFIELD - Query by Field query CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG Header;
   DWORD dwFlags;       /* flags (QUERYBYFIELD_FLAG_xxx) */
   WORD wDataType;      /* data type of field to search */
   WORD wOperator;      /* operation QUERYBYFIELD_OP_xxx */
   TIMEDATE Date1;      /* first operand */
   TIMEDATE Date2;      /* second operand */
   ALIGNED_NUMBER Number1; /* first operand */
   ALIGNED_NUMBER Number2; /* second operand */
   WORD wFieldNameLen;  /* length of field name */
   WORD wValueLen;      /* length of value */
	 /* field name follows */
	 /* value follows */
} CDQUERYBYFIELD;

**Description :**

Field-level query information is stored in a CDQUERYBYFIELD record in fields of type TYPE_QUERY, usually the query field of an Agent.  The query field of an Agent is used to select documents to be operated on by the Agent.  This record consists of this data structure, followed by the field name and any value for the field query (in packed format).  The fields in this structure are:
<ul><br>

<ul>Header			Defines this composite data item as a CDQUERYBYFIELD item.<br>
dwFlags		Field query flags (see QUERYBYFIELD_FLAG_xxx).<br>
wDataType		Type of field to search (see TYPE_xxx).<br>
wOperator		Field query operation (see QUERYBYFIELD_OP_xxx).<br>
Date1			First TIMEDATE value for comparison.<br>
Date2			Second TIMEDATE value defining a range.<br>
Number1		First ALIGNED_NUMBER value for comparison.<br>
Number2		Second ALIGNED_NUMBER value defining a range.<br>
wFieldNameLen	Length of the field name.<br>
wValueLen		Length of the value.</ul>
<br>
This structure is followed by a packed string containing the field name and any field value.</ul>



**See Also :**
[QUERYBYFIELD_FLAG_xxx](/domino-c-api-docs/reference/Symb/QUERYBYFIELD_FLAG_xxx)
[QUERYBYFIELD_OP_xxx](/domino-c-api-docs/reference/Symb/QUERYBYFIELD_OP_xxx)
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
---
