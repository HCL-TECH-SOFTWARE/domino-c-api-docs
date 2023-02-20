##### Data Type : Agents
##### CDACTIONMODIFYFIELD - Modify Field action CD Record.
---
```
#include <queryods.h>
```
**Description :**

A CDACTIONMODIFYFIELD record is stored in fields of type TYPE_ACTION, usually 
the action field of an Agent.  When the agent containing this action is run, 
the value of the specified field is modified in the notes selected by the 
Agent.  The fields in this structure are:

Header         Defines this composite data item as a
               CDACTIONMODIFYFIELD item.
dwFlags        Option flags (see MODIFYFIELD_FLAG_xxx)
wFieldNameLen  Length of the field name.
wValueLen      Length of the new value.

This structure is followed by packed strings containing the field name and the 
new value for the field.


**See Also :**
[MODIFYFIELD_FLAG_xxx](/reference/Symb/MODIFYFIELD_FLAG_xxx)
---
