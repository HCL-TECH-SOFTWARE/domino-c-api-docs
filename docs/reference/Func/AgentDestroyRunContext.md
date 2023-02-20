##### Function : Agents
##### AgentDestroyRunContext - Free the Agent run-time context.
---
```
#include <agents.h>
void LNPUBLIC AgentDestroyRunContext(

	HAGENTCTX  hAgentCtx);
```
**Description :**

Delete the Agent run-time context, free any resources allocated for this 
context, and close the handle.

**Parameters :**
Input :
hAgentCtx  -  Handle to the Agent run-time context.



**See Also :**
[AgentCreateRunContext](/reference/Func/AgentCreateRunContext)
[AgentRun](/reference/Func/AgentRun)
[HAGENTCTX](/reference/Data/HAGENTCTX)
---
