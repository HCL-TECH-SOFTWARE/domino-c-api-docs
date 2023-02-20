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
[AgentOpen](/reference/Func/AgentOpen)
[AgentRun](/reference/Func/AgentRun)
[HAGENT](/reference/Data/HAGENT)
---
