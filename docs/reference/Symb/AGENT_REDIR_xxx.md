##### Symbolic Value : Agents
##### AGENT_REDIR_xxx - Definitions for stdout redirection types.
---
```
#include <agents.h>
```

**Symbolic Values :**

	AGENT_REDIR_NONE	  -  Goes to the bit bucket.

	AGENT_REDIR_LOG	  -  Goes to the log file (default).

	AGENT_REDIR_MEMORY	  -  Goes to a memory buffer, cleared each AgentRun.

	AGENT_REDIR_MEMAPPEND	  -  Goes to buffer, append mode for each agent.


**Description :**

This specifies where output from the LotusScript &quot;print&quot; statement will go.


**See Also :**
[AgentRedirectStdout](/domino-c-api-docs/reference/Func/AgentRedirectStdout)
---
