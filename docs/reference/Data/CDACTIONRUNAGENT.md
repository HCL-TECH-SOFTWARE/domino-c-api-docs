##### Data Type : Agents
##### CDACTIONRUNAGENT - Run agent action CD record.
---
```
#include <queryods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   DWORD dwFlags;       /* flags */
   WORD  wAgentNameLen; /* Agent name length */
   WORD  wSpare;
/* agent name follows */
} CDACTIONRUNAGENT;

**Description :**

The action to run another Agent is stored in a CDACTIONRUNAGENT record in fields of type TYPE_ACTION, usually the action field of an Agent.  This record consists of this data structure, followed by the name of the agent.  The fields in this structure are:
<ul><br>

<ul>Header			Defines this composite data item as a CDACTIONRUNAGENT item.<br>
dwFlags		Reserved;  must be 0.<br>
wAgentNameLen	Length of the agent name (in bytes).<br>
wSpare		Reserved;  must be 0.</ul>
<br>
This structure is followed by a packed string containing the agent name.</ul>



**See Also :**
[CDACTION](/domino-c-api-docs/reference/Data/CDACTION)
---
