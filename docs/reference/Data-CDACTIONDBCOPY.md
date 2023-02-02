##### Data Type : Agents
##### CDACTIONDBCOPY - Database Copy action CD record.
---
##### #include <queryods.h>
**Description :**
A CDACTIONDBCOPY record is stored in fields of type TYPE_ACTION, usually the 
action field of an Agent.  When the agent containing this action is run, a copy 
of the data selected by the agent is placed in the named database.  The fields 
in this structure are:

Header  Defines this composite data item as a CDACTIONDBCOPY item.
dwFlags Option flags (see ACTIONDBCOPY_FLAG_xxx)
wServerLen Length of the server name
wDatabaseLen Length of the database name

This structure is followed by packed strings containing the server name and 
database name.
**See Also :**
[ACTIONDBCOPY_FLAG_xxx](D:/md_files/ACTIONDBCOPY_FLAG_xxx.md)
---
