##### Function : OOO
##### OOOInit - This function initializes global memory used for the caching of some internal information.
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOInit(
void);
```
**Description :**

This function initializes global memory used for the caching of some internal 
information,it should be called prior to calling any other OOO functions at 
application start. 

**Parameters :**

Output :
(routine)  -  Status code: 
NOERROR on success. 
An ERR status on failure indicating the problem. 



**See Also :**
[OOOTerm](/domino-c-api-docs/reference/Func/OOOTerm)
---
