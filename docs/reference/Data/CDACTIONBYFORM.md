##### Data Type : Agents
##### CDACTIONBYFORM - Form action CD record.
---
```
#include <queryods.h>
```
**Description :**

Actions associated with a form are stored in a CDACTIONBYFORM record in fields 
of type TYPE_ACTION, usually the action field of an Agent.  This record 
consists of this data structure, followed by field actions specified by 
ODS_ASSISTFIELDSTRUCT records, then followed by the name of the form.  The 
fields in this structure are:

Header  Defines this composite data item as a CDACTIONBYFORM item.
dwFlags  Form action flags (see ACTIONBYFIELD_OP_xxx or QUERYBYFIELD_OP_xxx).
wFieldCount  Number of fields that follow (number of ODS_ASSISTFIELDSTRUCT 
records).
wFormNameLen Length of the form name.

This structure is followed by the ODS_ASSISTFIELDSTRUCT structures, then a 
packed string containing the form name.

**See Also :**
[ACTIONBYFIELD_OP_xxx](/domino-c-api-docs/reference/Symb/ACTIONBYFIELD_OP_xxx)
[ODS_ASSISTFIELDSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTFIELDSTRUCT)
---
