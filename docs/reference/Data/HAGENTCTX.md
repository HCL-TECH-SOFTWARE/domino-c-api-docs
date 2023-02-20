##### Data Type : Agents
##### HAGENTCTX - Handle to an Agent runtime context.
---
```
#include <agents.h>
```
**Description :**

In order to actually run an agent, a "runtime context" must be created.  This 
context maintains information specific to a single execution of the agent.  The 
agent runtime context is created with the function AgentCreateRunContext(), and 
must be freed with the function AgentDestroyRunContext().

**See Also :**
[AgentCreateRunContext](/reference/Func/AgentCreateRunContext)
[AgentDestroyRunContext](/reference/Func/AgentDestroyRunContext)
[AgentRun](/reference/Func/AgentRun)
---
