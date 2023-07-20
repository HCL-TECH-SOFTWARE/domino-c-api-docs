##### Symbolic Value : Agents
##### AGENT_xxx - AgentRun - dwFlags
---
```
#include <agents.h>
```

**Symbolic Values :**

	AGENT_REOPEN_DB	  -  If AGENT_REOPEN_DB is set, the AgentRun call will reopen the agent's database with the privileges of the signer of the agent. If the flag is not set, the agent's "context" database will be open with the privileges of the current user (the current Notes id or the current Domino web user).


**Description :**

Possible values for the dwFlags parameter of AgentRun.


**See Also :**
[AgentRun](/domino-c-api-docs/reference/Func/AgentRun)
---
