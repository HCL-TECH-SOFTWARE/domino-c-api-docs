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
[AgentCreateRunContext](/domino-c-api-docs/reference/Func/AgentCreateRunContext)
[AgentRun](/domino-c-api-docs/reference/Func/AgentRun)
[HAGENTCTX](/domino-c-api-docs/reference/Data/HAGENTCTX)
---
