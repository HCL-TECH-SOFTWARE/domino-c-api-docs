##### Symbolic Value : Agents
##### AGENT_SECURITY_xxx - AgentCreateRunContext - dwFlags
---
```
#include <agents.h>
```

**Symbolic Values :**

	AGENT_SECURITY_OFF	  -  Turn off the security option for this run context.

	AGENT_SECURITY_ON	  -  This flag tells the run context that when it runs an agent, check the privileges of the signer of that agent and apply them. For example, if the signer of the agent has "restricted" agent privileges, then the agent will be restricted. If you do not set this flag, all agents run as unrestricted. This flag enables the following security checks:
 Restricted/unrestricted agent
 Can create databases
 Is agent targeted to this machine
 Is user allowed to access this machine
 Can user run personal agents


**Description :**

Possible values for the dwFlags parameter in AgentCreateRuncontext.  Specifies to the run context when it runs an agent, whether to check the privileges of the signer and apply them.


**See Also :**
[AgentCreateRunContext](/domino-c-api-docs/reference/Func/AgentCreateRunContext)
---
