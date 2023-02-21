##### Function : OOO
##### OOOGetState - This function returns the version (agent, service) and the state (disabled, enabled) of the out of office functionality.
---
```
#include <oooapi.h>
STATUS LNPUBLIC OOOGetState(

	OOOCTXPTR *pOOOContext,
	WORD *retVersion,
	WORD *retState);
```
**Description :**

This function returns the version (agent, service) and the state (disabled, 
enabled) of the out of office functionality.The version information can be used 
to show or hide UI elements that might not be supported for a given version.  
For example, the agent does not support durations of less than 1 day and some 
clients might choose not to show the hours in the user interface.When you need 
to make OOOGetState as efficient as possible, call OOOStartOperation with the 
home mail server and the handle to the opened mail database. This function is 
read only and does not return an error if user ACL rights are below Editor 
(which are required to turn on/off the Out of office functionality).If  
OOOGetState is called immediately following OOOEnable it will not reflect the 
state set by the OOOEnable.   To see the current state call OOOEndOperation and 
start a new operation  using OOOStartOperation, OOOGetState, OOOEndOperation.

**Parameters :**
Input :
pOOOContext  -  Pointer obtained from the OOOStartOperation call

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. 
NOERROR - Successfully perform this function.
This function can return Domino errors.
OOO specific errors:
ERR_OOO_MISSING_INIT - OOOGetState was called prior to OOOInit()
ERR_OOO_MISSING_PARAM - One or more mandatory parameters were not specified
ERR_OOO_MISSING_MAILFILE - Mailfile information is not specified


retVersion  -  The address of a WORD into which the version number is returned.
Required parameter.
Values for retVersion
#define  	OOO_CONFIG_AGENT           1
#define	OOO_CONFIG_SERVICE		2

retState  -  The address of a WORD into which the version number is returned.
Optional parameter. Pass in NULL if not interested in this information.
Values for retState
#define OOO_STATE_ENABLED		1
#define OOO_STATE_DISABLED		0


**See Also :**
[OOOEndOperation](/domino-c-api-docs/reference/Func/OOOEndOperation)
[OOOStartOperation](/domino-c-api-docs/reference/Func/OOOStartOperation)
---
