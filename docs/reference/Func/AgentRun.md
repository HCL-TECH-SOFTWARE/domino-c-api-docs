##### Function : Agents
##### AgentRun - Run an Agent.
---
```
#include <agents.h>
STATUS LNPUBLIC AgentRun(

	HAGENT  hAgent,
	HAGENTCTX  hAgentCtx,
	DHANDLE  hSelection,
	DWORD  dwFlags);
```
**Description :**

Given a handle to an open Agent (created by calling AgentOpen()) and a handle 
to an Agent runtime context (created by calling AgentCreateRunContext()), run 
the agent.

If the agent is not a LotusScript agent and it requires input from the UI, (for 
example the agent is to run on seclected documents), you will get the error, 
ERR_AGENT_UI_TRIGGER:  "Unsupported trigger and search in the background or 
embedded agent"

If a background agent erroneously refers to the UI (front-end) classes, you 
will get an error.

**Parameters :**
Input :
hAgent  -  Handle to the open Agent.

hAgentCtx  -  Handle to the Agent run-time context.

hSelection  -  Reseved;  must be 0.

dwFlags  -  Optional - can be 0.  See AGENT_xxx for other possible values.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_xxx - STATUS returned from a lower-level unction call.



**Sample Usage :**
```
/* Given the handle of the database and the Agent name, find the Note ID for 
the Agent.*/
 status = NIFFindDesignNote (hDb, pAgentName, NOTE_CLASS_FILTER, &AgentID);
 if (status == ERR_NOT_FOUND)
  status = NIFFindPrivateDesignNote (hDb, pAgentName, NOTE_CLASS_FILTER, 
&AgentID);
 
/* Open the Agent */ 
	status = AgentOpen (hDb, AgentId, &hOpenAgent);

/* Create the Agent Run Context */
	status = AgentCreateRunContext (hOpenAgent, NULL, (DWORD) 0, 
&hOpenAgentCtx);

/* Run the Agent */
	status = AgentRun (hOpenAgent, hOpenAgentCtx, (DHANDLE) 0, (DWORD) 0);

/* Destroy the Agent Run Context */
	AgentDestroyRunContext (hOpenAgentCtx);

/* Close the Agent */
	AgentClose (hOpenAgent);

```
**See Also :**
[AgentCreateRunContext](/reference/Func/AgentCreateRunContext)
[AgentOpen](/reference/Func/AgentOpen)
[HAGENT](/reference/Data/HAGENT)
[HAGENTCTX](/reference/Data/HAGENTCTX)
---
