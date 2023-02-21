##### Data Type : Agents
##### CDACTIONDELETE - Delete action CD record.
---
```
#include <queryods.h>
```
**Description :**

A CDACTIONDELETE record is stored in fields of type TYPE_ACTION, usually the 
action field of an Agent.  When the agent containing this action is run, the 
data selected by the agent is deleted.  The fields in this structure are:

Header  Defines this composite data item as a CDACTIONDELETE item.
dwFlags Reserved;  must be 0.


**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
