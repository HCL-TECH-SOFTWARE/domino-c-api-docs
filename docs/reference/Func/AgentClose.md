##### Function : Agents
##### AgentClose - Close an open Agent.
---
```
#include <agents.h>
void LNPUBLIC AgentClose(

	HAGENT  hAgent);
```
**Description :**

Close the Agent, which was opened by AgentOpen(), and release any system 
resources assigned to this handle.

**Parameters :**
Input :
hAgent  -  Handle to an open Agent.



**See Also :**
[AgentOpen](/domino-c-api-docs/reference/Func/AgentOpen)
[AgentRun](/domino-c-api-docs/reference/Func/AgentRun)
[HAGENT](/domino-c-api-docs/reference/Data/HAGENT)
---
