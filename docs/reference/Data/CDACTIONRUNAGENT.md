##### Data Type : Agents
##### CDACTIONRUNAGENT - Run agent action CD record.
---
```
#include <queryods.h>
```
**Description :**

The action to run another Agent is stored in a CDACTIONRUNAGENT record in 
fields of type TYPE_ACTION, usually the action field of an Agent.  This record 
consists of this data structure, followed by the name of the agent.  The fields 
in this structure are:

Header   Defines this composite data item as a CDACTIONRUNAGENT item.
dwFlags  Reserved;  must be 0.
wAgentNameLen Length of the agent name (in bytes).
wSpare  Reserved;  must be 0.

This structure is followed by a packed string containing the agent name.

**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
