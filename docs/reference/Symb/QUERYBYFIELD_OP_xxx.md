##### Symbolic Value : Agents
##### QUERYBYFIELD_OP_xxx - Comparison operators for field-level query.
---
```
#include <queryods.h>
```

**Symbolic Values :**

	QUERYBYFIELD_OP_GREATER	  -  Select document if field is greater than value.

	QUERYBYFIELD_OP_LESS	  -  Select document if field is less than value.

	QUERYBYFIELD_OP_NOTEQUAL	  -  Select document if field is not equal to value.

	QUERYBYFIELD_OP_BETWEEN	  -  Select document if field is in specified range (between Date1 and Date2 for TYPE_TIME, between Number1 and Number2 for TYPE_NUMBER).

	QUERYBYFIELD_OP_NOTWITHIN	  -  Select document if field is not in the specified range.

	QUERYBYFIELD_OP_EQUAL	  -  Select document if field is equal to value.

	QUERYBYFIELD_OP_CONTAINS	  -  Select document if field contains the specified value.

	QUERYBYFIELD_OP_DOESNOTCONTAIN	  -  Select document if field does not contain the specified value.

	QUERYBYFIELD_OP_INTHELAST	  -  Select document if the field value is within the last n days.

	QUERYBYFIELD_OP_INTHENEXT	  -  Select document if the field value is within the next n days.

	QUERYBYFIELD_OP_OLDERTHAN	  -  Select document if the field value is older than n days.

	QUERYBYFIELD_OP_DUEIN	  -  Select document if the field value is due more than n days from now.


**Description :**

These operators are specified in the wOperator field of the CDQUERYBYFIELD record.  The operator code identifies how the value of the field in the document is to be tested against the field value supplied in the query record.


**See Also :**
[CDQUERYBYFIELD](/domino-c-api-docs/reference/Data/CDQUERYBYFIELD)
---
