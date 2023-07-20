##### Data Type : Agents
##### HAGENT - Handle to an open Agent.
---
```
#include <agents.h>
```

**Definition :**
```
typedef void far *HAGENT;
```

**Description :**

An Agent handle is used to refer to an open agent.  The Agent handle is created by AgentOpen(), and must be released by a call to AgentClose().


**See Also :**
[AgentClose](/domino-c-api-docs/reference/Func/AgentClose)
[AgentCreateRunContext](/domino-c-api-docs/reference/Func/AgentCreateRunContext)
[AgentOpen](/domino-c-api-docs/reference/Func/AgentOpen)
[AgentRun](/domino-c-api-docs/reference/Func/AgentRun)
---
