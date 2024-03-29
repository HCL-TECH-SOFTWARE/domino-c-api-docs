##### Function : Agents
##### AgentSetTimeExecutionLimit - Set time limit for Agent execution.
---
```
#include <agents.h>
STATUS LNPUBLIC AgentSetTimeExecutionLimit(

	HAGENTCTX  hAgentCtx,
	DWORD  timeLimit);
```
**Description :**

Allow API users to set time limit for Agent execution.  If the time limit is 
not set, the default is 0 which means no time limit for the execution.  

If an agent takes less than the specified time limit when a time limit is not 
set, then if that specified time limit is set, the call to AgentRun for this 
agent will take up the full amount of the time limit.

**Parameters :**
Input :
hAgentCtx  -  Handle to the Agent.

timeLimit  -  Time limit, in seconds, for the execution.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is.  The return error codes include:

NOERROR

ERR_xxx - Error returned by lower level functions. Call OSLoadString to interpret code.



**See Also :**
[AgentCreateRunContext](/domino-c-api-docs/reference/Func/AgentCreateRunContext)
---
