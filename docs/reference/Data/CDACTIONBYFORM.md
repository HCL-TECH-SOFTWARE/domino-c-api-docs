##### Data Type : Agents
##### CDACTIONBYFORM - Form action CD record.
---
```
#include <queryods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;
   DWORD dwFlags;
   WORD  wFieldCount;  /* Number of fields that follow */
   WORD  wFormNameLen; /* Length of form name */
	 /* ODS_ASSISTFIELDSTRUCTs follow */
	 /* Form name follows */
} CDACTIONBYFORM;
```

**Description :**

Actions associated with a form are stored in a CDACTIONBYFORM record in fields of type TYPE_ACTION, usually the action field of an Agent.  This record consists of this data structure, followed by field actions specified by ODS_ASSISTFIELDSTRUCT records, then followed by the name of the form.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDACTIONBYFORM item.<br>
dwFlags		Form action flags (see ACTIONBYFIELD_OP_xxx or QUERYBYFIELD_OP_xxx).<br>
wFieldCount		Number of fields that follow (number of ODS_ASSISTFIELDSTRUCT records).<br>
wFormNameLen	Length of the form name.</ul>
<br>
This structure is followed by the ODS_ASSISTFIELDSTRUCT structures, then a packed string containing the form name.</ul>



**See Also :**
[ACTIONBYFIELD_OP_xxx](/domino-c-api-docs/reference/Symb/ACTIONBYFIELD_OP_xxx)
[ODS_ASSISTFIELDSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTFIELDSTRUCT)
---
