##### Symbolic Value : Agents
##### ACTIONREPLY_FLAG_xxx - Option flags for CDACTIONREPLY record.
---
```
#include <queryods.h>
```

**Symbolic Values :**

	ACTIONREPLY_FLAG_REPLYTOALL	  -  Send reply to all (otherwise, just to sender).

	ACTIONREPLY_FLAG_INCLUDEDOC	  -  Include a copy of the original document.

	ACTIONREPLY_FLAG_SAVEMAIL	  -  Save a copy of the reply.

	ACTIONREPLY_FLAG_NOAGENTREPLY	  -  Do not reply to agent-generated mail.

	ACTIONREPLY_FLAG_REPLYONCE	  -  Only reply once per sender.


**Description :**

These flags specify options for the Reply action for a Agent.  These flags are stored in the dwFlags field of the CDACTIONREPLY structure.


**See Also :**
[CDACTIONREPLY](/domino-c-api-docs/reference/Data/CDACTIONREPLY)
---
