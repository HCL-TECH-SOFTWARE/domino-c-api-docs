##### Data Type : Agents
##### CDQUERYBYFORM - Query by Form query CD record.
---
##### #include <queryods.h>
**Description :**
Queries associated with a form are stored in a CDQUERYBYFORM record in fields 
of type TYPE_QUERY, usually the query field of an Agent.  This record consists 
of this data structure, followed by field actions specified by 
ODS_ASSISTFIELDSTRUCT records, then followed by the name of the form.  The 
fields in this structure are:

Header  Defines this composite data item as a CDQUERYBYFORM item.
dwFlags  Reserved;  must be 0.
wFieldCount  Number of fields that follow (number of ODS_ASSISTFIELDSTRUCT 
records).
wFormNameLen Length of the form name.

This structure is followed by the ODS_ASSISTFIELDSTRUCT structures, then a 
packed string containing the form name.
**See Also :**
[ODS_ASSISTFIELDSTRUCT](D:/md_files/ODS_ASSISTFIELDSTRUCT.md)
---
