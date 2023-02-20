##### Function : OOO
##### OOOSetAwayPeriod - This function validates and sets the time parameters that control OOO. 
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOSetAwayPeriod(

	OOOCTXPTR *pOOOContext,
	TIMEDATE  tdStartAway,
	TIMEDATE  tdEndAway);
```
**Description :**

This function validates and sets the time parameters that control OOO.  This 
information is required for enabling the OOO. 
	If you want turn on OOO functionality for a given period of time the 
sequence of calls needed is: OOOStartOperation, OOOSetAwayPeriod, OOOEnable, 
OOOEndOperation.  

	When you need to enable OOO (i.e. call it with bState flag set to TRUE) 
you should call OOOSetAwayPeriod prior to calling OOOEnable.  

	If you need to change the length of the away period after OOO has 
already been enabled, the sequence of calls needed to perform this action is  
OOOStartOperation, OOOSetAwayPeriod, OOOEndOperation.  

	If the Domino server is configured to run an OOO agent, it can only be 
turned on for full days, the time portion of the date parameter will not be 
used.

**Parameters :**
Input :
pOOOContext  -  Pointer obtained from the OOOStartOperation call

tdStartAway  -  This is date and time when Out of office will begin.

tdEndAway  -  This is date and time when Out of office will end.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. 
NOERROR - Successfully performed this operation
This function can return Domino errors.
OOO specific errors:
ERR_OOO_MISSING_PARAM - One or more mandatory parameters were not specified
ERR_OOO_MISSING_MAILFILE - Mailfile information is not specified



**See Also :**
[OOOGetAwayPeriod](/reference/Func/OOOGetAwayPeriod)
---
