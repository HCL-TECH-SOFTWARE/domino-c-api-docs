##### Function : Domino Upgrade Services
##### DUSTerm - Terminate this DUS DLL.
---
```
#include <dus.h>
STATUS LNCALLBACK DUSTerm(
void);
```
**Description :**

This call notifies the DUS DLL that is being terminated.  Any allocated memory 
not already freed should be freed here.

**Parameters :**

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
---
