##### Data Type : Agents
##### CDQUERYUSESFORM - Query using form query CD record.
---
##### #include <queryods.h>
**Description :**
The names of the forms to be used in a query are stored in CDQUERYUSESFORM 
records in fields of type TYPE_QUERY, usually the query field of an Agent.  The 
fields in this structure are:

Header  Defines this composite data item as a CDQUERYUSESFORM item.
dwFlags  Reserved;  must be 0.

This structure is followed by LIST structure containing the form names.
**See Also :**
[LIST](D:/md_files/LIST.md)
---
