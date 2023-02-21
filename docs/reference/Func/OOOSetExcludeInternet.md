##### Function : OOO
##### OOOSetExcludeInternet - This function sets a flag which defines how to treat internet emails. 
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOSetExcludeInternet(

	OOOCTXPTR *pOOOContext,
	BOOL  bExcludeInternet);
```
**Description :**

This function sets a flag which defines how to treat internet emails.  This 
functional call is optional.   If this flag is set to TRUE OOO notifications 
will not be generated for email originating from the internet.  The default for 
this flag is TRUE.

**Parameters :**
Input :
pOOOContext  -  Pointer obtained from the OOOStartOperation call

bExcludeInternet  -  Flag to ignore internet emails when set to TRUE

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. 
NOERROR - Successfully performed this operation



**See Also :**
[OOOGetExcludeInternet](/domino-c-api-docs/reference/Func/OOOGetExcludeInternet)
---
