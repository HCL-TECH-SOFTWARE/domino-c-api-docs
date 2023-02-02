##### Function : Agents
##### AgentSetHttpStatusCode - Set an agent's return http status code.
---
##### #include <agents.h>
STATUS **AgentSetHttpStatusCode(**

	HAGENTCTX  hAgentCtx,
	DWORD  retStatus);
**Description :**
Set an agent's return HTTP status code. This must be a http status code as 
defined by http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html and supported 
by the web server.
**Parameters :**
Input :
hAgentCtx  -  The agent context.

retStatus  -  The http status code.

Output :
(routine)  -  Returns status from the call, either success or an error.


**Sample Usage :**
```
	/* Assumes HAGENTCTX and DWORD http status code where kResultsOK = 
200.*/

  AgentSetHttpStatusCode(HAgentCtx, kResultsOK); 
```
**See Also :**
[](D:/md_files/.md)
---
