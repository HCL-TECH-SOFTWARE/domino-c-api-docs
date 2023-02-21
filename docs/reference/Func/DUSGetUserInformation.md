##### Function : Domino Upgrade Services
##### DUSGetUserInformation - Get Full User Information for this User to be migrated.
---
```
#include <dus.h>
STATUS LNCALLBACK DUSGetUserInformation(

	DHANDLE  hContext,
	char *UserName,
	NOTEHANDLE  hUserNote,
	DWORD  TotalLeftToRead);
```
**Description :**

This call supplies the upgrade DLL with full user information for the user 
selected.

**Parameters :**
Input :
hContext  -  Handle to this DUS' specific context information.

UserName  -  Name of the user to obtain information for.  Originally supplied to the DUS framework with DUSRetrieveUsers().

hUserNote  -  Handle to the note which contains the User information requested.  It is used by the DUS to identify the user for which full information is being requested.  The hUserNote should NOT be updated or closed by the DUS.  The DUS framework (caller) writes additional fields to this note and will update/close the hUserNote appropriately. 

TotalLeftToRead  -  The number of selected users for which full information still needs to be returned by the DUS.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.



**See Also :**
[DUSGetGroupInformation](/domino-c-api-docs/reference/Func/DUSGetGroupInformation)
---
