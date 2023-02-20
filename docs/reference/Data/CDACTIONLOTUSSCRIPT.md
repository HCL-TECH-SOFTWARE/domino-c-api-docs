##### Data Type : Agents
##### CDACTIONLOTUSSCRIPT - LotusScript action CD record.
---
```
#include <queryods.h>
```
**Description :**

A CDACTIONLOTUSSCRIPT record is stored in fields of type TYPE_ACTION, such as 
in the action field of an Agent.  This record contains LotusScript commands 
that will be executed when the agent is run.  The fields in this structure are:

Header  Defines this composite data item as a CDACTIONLOTUSSCRIPT item.
dwFlags Option flags - reserved;  must be 0.
wScriptLen Length of LotusScript commands.

This structure is followed by the LotusScript commands.


**See Also :**
[CDACTION](/reference/Data/CDACTION)
---
