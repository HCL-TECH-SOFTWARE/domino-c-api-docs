##### Function : Extension Manager
##### TerminateNSFEMCallback - Extension Manager callback for EM_TERMINATENSF
---
```
#include <extmgr.h>
void LNPUBLIC TerminateNSFEMCallback(

	void *unused_params);
```
**Description :**

EM_TERMINATENSF occurs when NSF service terminates for the process, right 
before the extension manager DLLs are unloaded.  

Do not de-register callback functions in the callback routine for the 
EM_TERMINATENSF notification.

**Parameters :**
Input :
unused_params  -  Reserved for future use.



**See Also :**
[EM_xxx](/reference/Symb/EM_xxx)
---
