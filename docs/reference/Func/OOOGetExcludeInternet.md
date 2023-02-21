##### Function : OOO
##### OOOGetExcludeInternet - This function returns a flag which defines how to treat internet emails. 
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOGetExcludeInternet(

	OOOCTXPTR *pOOOContext,
	BOOL *bExcludeInternet);
```
**Description :**

This function returns a flag which defines how to treat internet emails.  This 
functional call is optional.   If this flag is set to TRUE OOO notifications 
will not be generated for email originating from the internet.  The default for 
this flag is TRUE.

**Parameters :**
Input :
pOOOContext  -  Pointer obtained from the OOOStartOperation call

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. 
NOERROR - Successfully performed this operation


bExcludeInternet  -  Pointer to flag that indicates whether to ignore internet emails 


**See Also :**
[OOOSetExcludeInternet](/domino-c-api-docs/reference/Func/OOOSetExcludeInternet)
---
