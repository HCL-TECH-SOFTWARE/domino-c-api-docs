##### Function : Agents
##### AgentCreateRunContextExt - Create a run context for a given agent.
---
```
#include <agents.h>
STATUS AgentCreateRunContextExt(

	HAGENT  hAgent,
	void *pReserved,
	HAGENTCTX  pOldContext,
	DWORD  dwFlags,
	HAGENTCTX  rethContext);
```
**Description :**

Create a run context for a given agent.

**Parameters :**
Input :
hAgent  -  An open agent returned by AgentOpen. If null, the Init call is deferred until run time.

pReserved  -  Passes a run context object to clone when available.

pOldContext  -  Top-level agent context to pass required values. Set to NULL for top-level agents.

dwFlags  -  dwFlags  -  Optional.  Use this flag to tell the run context that when it runs an agent, you want it to check the privileges of the signer of that agent and apply them.  For example, if the signer of the agent has "restricted" agent privileges, then the agent will be restricted.  If you do not set this flag, all agents run as unrestricted.

List of security checks enabled by this flag:
	Restricted/unrestricted agent.
	Can create databases.
	Is agent targeted to this machine.
	Is user allowed to access this machine.
	Can user run personal agents.

Output :
(routine)  -  Returns status from the call, either success or an error.


rethContext  -  The context to be returned.


**Sample Usage :**
```
	HAGENT hagent = NULLHANDLE;
	HAGENTCTX hagentctx = (HAGENTCTX)NULL;
  void * pactionctx = NULL; 
	pactionctx = (LPVOID)s->ANSGetActionCtx(); 

	/* Present context of current agent to improved constructor which will 
pull selected members out of the class to construct the new action context. 
	note that input may be either a cdefactionctx or a webactionctx. output 
will always be a webactionctx. */ 

	stat = ::AgentCreateRunContextExt(hagent, (void far *) NULL, 
pactionctx, (DWORD)AGENT_SECURITY_ON, &hagentctx);
 
	/* Agentcreateruncontextext call has set namelist based on runaswebuser 
agent design flag. */ 
	
	if (stat == NOERROR)
	{
   /* ANSIsWebSession is true when the back-end session is created on behalf of 
an internet user. */
   if ((::IsRunAsWebUser(hagent)) && (s->ANSIsWebSession()))
   { 
	  DHANDLE hNamesList = s->ANSGetNamesList();

    PDEFACTIONCTX pActionCtx = (PDEFACTIONCTX)hagentctx;
    pActionCtx->SetNameList(hNamesList); 
	 } 
	}
```
**See Also :**
---
