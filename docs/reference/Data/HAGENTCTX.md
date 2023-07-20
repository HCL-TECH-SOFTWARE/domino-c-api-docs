##### Data Type : Agents
##### HAGENTCTX - Handle to an Agent runtime context.
---
```
#include <agents.h>
```

**Definition :**
```
typedef void far *HAGENTCTX;
```

**Description :**

In order to actually run an agent, a &quot;runtime context&quot; must be created.  This context maintains information specific to a single execution of the agent.  The agent runtime context is created with the function AgentCreateRunContext(), and must be freed with the function AgentDestroyRunContext().


**See Also :**
[AgentCreateRunContext](/domino-c-api-docs/reference/Func/AgentCreateRunContext)
[AgentDestroyRunContext](/domino-c-api-docs/reference/Func/AgentDestroyRunContext)
[AgentRun](/domino-c-api-docs/reference/Func/AgentRun)
---
