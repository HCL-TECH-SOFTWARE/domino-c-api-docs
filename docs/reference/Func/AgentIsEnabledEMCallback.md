##### Function : Extension Manager
##### AgentIsEnabledEMCallback - Extension Manager callback for EM_AGENTISENABLED
---
```
#include <extmgr.h>
STATUS LNPUBLIC AgentIsEnabledEMCallback(

	HAGENT  hAgent,
	BOOL *return_value);
```
**Description :**

Though AgentIsEnabled is a publicly-defined function, its extension manager 
callback has a slightly different signature because of the fact that the public 
function returns BOOL instead of STATUS.  The extension manager callback has an 
added argument which allows the callback to write the return value of the API 
routine.  For purposes of the callback, it is as if the function signatures 
were as follows:

**Parameters :**
Input :
hAgent  -  Handle of Agent.

Output :
(routine)  -  
ERR_EM_CONTINUE


return_value  -  TRUE - agent is enabled.  FALSE - agent isn't enabled.


**See Also :**
[EM_xxx](/reference/Symb/EM_xxx)
---
