##### Function : Agents
##### AgentRedirectStdout - Set standard output redirection for LotusScript Agents
---
```
#include <agents.h>
STATUS LNPUBLIC AgentRedirectStdout(

	HAGENTCTX  hAgentCtx,
	WORD  redirType);
```
**Description :**

This routine is used to either disable standard output of LotusScript agent 
actions that use PRINT statements, or to redirect it to the log file or to an 
in-memory buffer.  The output of the PRINT statements is assigned to the 
specified runtime context, and is controlled by the redirType argument.    This 
argument can be set to one of the following constant values defined in 
agents.h, as described.

redirType Value Redirected Standard Output
AGENT_REDIR_NONE Disabled
AGENT_REDIR_LOG Log file (log.nsf)
AGENT_REDIR_MEMORY Memory buffer - reset with each call to AgentRun() 
AGENT_REDIR_MEMAPPEND Memory buffer - appended to with each call to AgentRun()

When redirecting to memory, you must call AgentQueryStdoutBuffer() after the 
agent execution to read the output buffer.   Since this redirection is 
associated with the runtime context, the desired action can be changed prior to 
each call to AgentRun().


**Parameters :**
Input :
hAgentCtx  -  Handle to the Agent runtime context.

redirType  -  Standard output redirection type.   Must be set to appropriate AGENT_REDIR_xxx value.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_xxx - STATUS returned from a lower-level function call.



**See Also :**
[AgentQueryStdoutBuffer](/reference/Func/AgentQueryStdoutBuffer)
[AgentRun](/reference/Func/AgentRun)
[AGENT_REDIR_xxx](/reference/Symb/AGENT_REDIR_xxx)
[HAGENTCTX](/reference/Data/HAGENTCTX)
---
