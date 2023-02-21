##### Data Type : Agents
##### ODS_ASSISTFIELDSTRUCT - Field actions associated with a form.
---
```
#include <queryods.h>
```
**Description :**

Within a CDACTIONBYFORM record, the actions for individual fields are specifed 
in an array of ODS_ASSISTFIELDSTRUCT structures.  The fields in this structure 
are:

wTotalLen  Length of this structure, including padding, in bytes
wOperator  Field operation - one of the ACTIONBYFIELD_OP_xxx or 
QUERYBYFIELD_OP_xxx values
wFieldNameLen Length of the field name
wValueLen  Length of the value
wValueDataType Reserved;  must be 0

This structure is followed by the field name, then the data for the new value.  
The value is stored as a text list, beginning with the type word containing 
TYPE_TEXT_LIST.

**See Also :**
[ACTIONBYFIELD_OP_xxx](/domino-c-api-docs/reference/Symb/ACTIONBYFIELD_OP_xxx)
[CDACTIONBYFORM](/domino-c-api-docs/reference/Data/CDACTIONBYFORM)
[QUERYBYFIELD_OP_xxx](/domino-c-api-docs/reference/Symb/QUERYBYFIELD_OP_xxx)
[CDQUERYBYFORM](/domino-c-api-docs/reference/Data/CDQUERYBYFORM)
---
