##### Function : OOO
##### OOOTerm - This function cleans up global memory used for caching of some internal information.
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOTerm(
void);
```
**Description :**

This function cleans up global memory used for caching of some internal 
information,it should be called when application is terminating.  

**Parameters :**

Output :
(routine)  -  Status code: 
NOERROR on success. 
An ERR status on failure indicating the problem. 



**See Also :**
[OOOInit](/domino-c-api-docs/reference/Func/OOOInit)
---
