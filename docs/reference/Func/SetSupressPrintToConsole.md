##### Function : Agents
##### SetSupressPrintToConsole - Allow api users to supress prints to server console.
---
```
#include <agents.h>
STATUS LNPUBLIC SetSupressPrintToConsole(

	HAGENTCTX hAgentCtx, 
	BOOL bFlag);
```
**Description :**

This routine allow api users to supress prints to server console (web agents want it for effeciency and reduce chattiness)
This can be used along with AgentRedirectStdout() to prevent logging information to the log where the admin/developer does not expect it to be. 
The log could contain sensitive information and overflow the logs

**Parameters :**
Input :

hAgentCtx - Handle to the Agent runtime context.

bFlag - TRUE if you don't want to log to console.FALSE, otherwise.

Output :

(routine) - Return indicates either success or what the error is. The return codes include:

NOERROR - Operation was successful.

ERR_xxx - STATUS returned from a lower-level function call.


**See Also :**
[AgentRedirectStdout](/domino-c-api-docs/reference/Func/AgentRedirectStdout)
[AgentRun](/domino-c-api-docs/reference/Func/AgentRun)
[AGENT_REDIR_xxx](/domino-c-api-docs/reference/Symb/AGENT_REDIR_xxx)
[HAGENTCTX](/domino-c-api-docs/reference/Data/HAGENTCTX)
---
