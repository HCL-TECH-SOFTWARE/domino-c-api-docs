##### Data Type : Agents
##### ODS_ASSISTFIELDSTRUCT - Field actions associated with a form.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WORD wTotalLen;      /* Total length of field structure
                           (includes padding) */
   WORD wOperator;      /* Query or action operator
                           (ACTIONBYFIELD_OP_xxx or
                            QUERYBYFIELD_OP_xxx) */
   WORD wFieldNameLen;  /* Field name length */
   WORD wValueLen;      /* Length of value */
   WORD wValueDataType; /* Reserved; must be 0 */
   WORD wSpare;
	 /* Field name follows */
	 /* Text list of values follows */
	 /* Padded to WORD boundary */
} ODS_ASSISTFIELDSTRUCT;

**Description :**

Within a CDACTIONBYFORM record, the actions for individual fields are specifed in an array of ODS_ASSISTFIELDSTRUCT structures.  The fields in this structure are:
<ul><br>

<ul>wTotalLen		Length of this structure, including padding, in bytes<br>
wOperator		Field operation - one of the ACTIONBYFIELD_OP_xxx or QUERYBYFIELD_OP_xxx values<br>
wFieldNameLen	Length of the field name<br>
wValueLen		Length of the value<br>
wValueDataType	Reserved;  must be 0</ul>
<br>
This structure is followed by the field name, then the data for the new value.  The value is stored as a text list, beginning with the type word containing TYPE_TEXT_LIST.</ul>



**See Also :**
[ACTIONBYFIELD_OP_xxx](/domino-c-api-docs/reference/Symb/ACTIONBYFIELD_OP_xxx)
[CDACTIONBYFORM](/domino-c-api-docs/reference/Data/CDACTIONBYFORM)
[QUERYBYFIELD_OP_xxx](/domino-c-api-docs/reference/Symb/QUERYBYFIELD_OP_xxx)
[CDQUERYBYFORM](/domino-c-api-docs/reference/Data/CDQUERYBYFORM)
---
