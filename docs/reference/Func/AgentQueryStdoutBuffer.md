##### Function : Agents
##### AgentQueryStdoutBuffer - Returns a Handle to redirected LotusScript Agent output.
---
```
#include <agents.h>
void LNPUBLIC AgentQueryStdoutBuffer(

	HAGENTCTX  hAgentCtx,
	DHANDLE FAR *retHdl,
	DWORD FAR *retSize);
```
**Description :**

This routine will return a handle and byte length of a buffer containing the 
redirected standard output of a LotusScript based agent.   Only output 
redirection to an in-memory buffer that has been configured for the specified 
Agent runtime context, via AgentRedirectStdout(), is accessible by this 
routine.

**Parameters :**
Input :
hAgentCtx  -  Handle to the Agent runtime context.

Output :
retHdl  -  Handle to redirected standard output buffer.   This handle is owned by Notes and must not be freed by the API program.

retSize  -  Byte length of retrieved buffer.


**Sample Usage :**
```
...
   HAGENT        hOpenAgent
   HAGENTCTX       hOpenAgentCtx
   DHANDLE          hStdout;
   DWORD           dwLen;
   char            *pStdout;
   STATUS          error = NOERROR;
...
   /* agent run handle and runtime context handle already created */
   error = AgentRedirectStdout (hOpenAgentCtx, AGENT_REDIR_MEMORY))
...   
   error = AgentRun (hOpenAgent, hOpenAgentCtx, (DHANDLE) 0, (DWORD) 0);
...
   AgentQueryStdoutBuffer (hOpenAgentCtx, &hStdout, &dwLen);
   pStdout = OSLock(char, hStdout);
   pStdout[dwLen]='\0';
   printf("Redirected PRINT statements:%s\n", pStdout);
   OSUnlock(hStdout);
...

```
**See Also :**
[AgentCreateRunContext](/domino-c-api-docs/reference/Func/AgentCreateRunContext)
[AgentRedirectStdout](/domino-c-api-docs/reference/Func/AgentRedirectStdout)
[HAGENTCTX](/domino-c-api-docs/reference/Data/HAGENTCTX)
---
