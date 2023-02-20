##### Function : Agents
##### AgentCreateRunContext - Create an Agent run-time context.
---
```
#include <agents.h>
STATUS LNPUBLIC AgentCreateRunContext(

	HAGENT  hAgent,
	void far *pReserved,
	DWORD  dwFlags,
	HAGENTCTX far *rethContext);
```
**Description :**

Create a run-time context for execution of the specified Agent.  This context 
maintains information about a single execution of the Agent, and must be 
created before the agent can be run.  This run-time context must be freed by 
calling AgentDestroyRunContext().

**Parameters :**
Input :
hAgent  -  Handle to the Agent.

pReserved  -  Reserved;  must be NULL.

dwFlags  -  Optional.  Use this flag to tell the run context that when it runs an agent, you want it to check the privileges of the signer of that agent and apply them.  For example, if the signer of the agent has "restricted" agent privileges, then the agent will be restricted.  If you do not set this flag, all agents run as unrestricted.

List of security checks enabled by this flag:
	Restricted/unrestricted agent
	Can create databases
	Is agent targeted to this machine
	Is user allowed to access this machine
	Can user run personal agents

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_xxx - STATUS returned from a lower-level function call.


rethContext  -  Handle to the Agent run-time context.


**See Also :**
[AgentDestroyRunContext](/reference/Func/AgentDestroyRunContext)
[AgentRun](/reference/Func/AgentRun)
[HAGENT](/reference/Data/HAGENT)
[HAGENTCTX](/reference/Data/HAGENTCTX)
---
