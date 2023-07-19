##### Data Type : Agents
##### CDQUERYBYFORM - Query by Form query CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG Header;
   DWORD dwFlags;
   WORD wFieldCount;  /* Number of fields that follow */
 WORD wFormNameLen; /* Length of form name */
  /* ODS_ASSISTFIELDSTRUCTs follow */
	 /* Form name follows */
} CDQUERYBYFORM;

**Description :**

Queries associated with a form are stored in a CDQUERYBYFORM record in fields of type TYPE_QUERY, usually the query field of an Agent.  This record consists of this data structure, followed by field actions specified by ODS_ASSISTFIELDSTRUCT records, then followed by the name of the form.  The fields in this structure are:
<ul><br>

<ul>Header		Defines this composite data item as a CDQUERYBYFORM item.<br>
dwFlags		Reserved;  must be 0.<br>
wFieldCount		Number of fields that follow (number of ODS_ASSISTFIELDSTRUCT records).<br>
wFormNameLen	Length of the form name.</ul>
<br>
This structure is followed by the ODS_ASSISTFIELDSTRUCT structures, then a packed string containing the form name.</ul>



**See Also :**
[ODS_ASSISTFIELDSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTFIELDSTRUCT)
---
