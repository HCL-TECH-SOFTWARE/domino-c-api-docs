##### Function : OOO
##### OOOEndOperation - This function frees memory.  
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOEndOperation(

	OOOCTXHANDLE  hOOContext,
	OOOCTXPTR *pOOOContext);
```
**Description :**

This function frees memory.  This function should be called after all other 
calls related to a specific operation(s) are completed.

**Parameters :**
Input :
hOOContext  -  Handle to the OOO context returned from OOOStartOperation call

pOOOContext  -  Pointer to the OOO context returned from OOOStartOperation call

Output :
(routine)  -  Return status from this call indicates either success or what the error is. 
NOERROR - Successfully perform this function.
This function can return Domino errors.



**See Also :**
[OOOStartOperation](/domino-c-api-docs/reference/Func/OOOStartOperation)
---
