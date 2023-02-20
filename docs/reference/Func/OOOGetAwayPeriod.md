##### Function : OOO
##### OOOGetAwayPeriod - This function returns time parameters that control OOO. 
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOGetAwayPeriod(

	OOOCTXPTR *pOOOContext,
	TIMEDATE *tdStartAway,
	TIMEDATE *tdEndAway);
```
**Description :**

This function returns time parameters that control OOO. 

**Parameters :**
Input :
pOOOContext  -  Pointer obtained from the OOOStartOperation call

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is.
NOERROR - Successfully performed this operation
This function can return Domino errors.
OOO specific errors:
ERR_OOO_MISSING_PARAM - One or more mandatory parameters were not specified
ERR_OOO_MISSING_MAILFILE - Mailfile information is not specified


tdStartAway  -  Pointer to the date and time when Out of office will begin.

tdEndAway  -  Pointer to the date and time when Out of office will end.


**See Also :**
[OOOSetAwayPeriod](/reference/Func/OOOSetAwayPeriod)
---
