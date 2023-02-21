##### Function : Domino Upgrade Services
##### DUSRetrieveUsers - Retrieve Users within an array of DUS_ENTRY structs, for upgrade/migration.
---
```
#include <dus.h>
STATUS LNCALLBACK DUSRetrieveUsers(

	DHANDLE  hContext,
	DWORD  StartIndex,
	DWORD *pResumeIndex,
	DWORD  NumUsersRequested,
	DWORD *pNumUsersReturned,
	DHANDLE *pRethExternalUsers,
	DWORD *pRetUserEntrySize);
```
**Description :**

This function allocates and passes back an array of DUS_ENTRY structs 
containing information about the users available for upgrade/migration.  
DUSRetrieveUsers() will continue to be called by the DUS framework until the 
DUS returns a resume index of 0 or the *pNumUsersReturned is less than 
*pNumUsersRequested.

**Parameters :**
Input :
hContext  -  Handle to this DUS' specific context information.

StartIndex  -  Set to 0L the first time the DUS is called.  If all users are not retrieved the first time and subsequent calls are necessary, this value is equal to the resume index passed back by the DUS on the previous call.

NumUsersRequested  -  Number of users provided to the caller.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


pResumeIndex  -  Set this value if additional users need to be returned to the DUS framework.  This value will be returned to the DUS on the subsequent DUSRetrieveUsers() call as the StartIndex.  When user retrieval is complete the pResumeIndex should be set to 0L.

pNumUsersReturned  -  Points to the number of users returned by the DUS to the caller.  This value should be used to allocate an array of DUS_ENTRY structs with the size (NumUsersRequested * sizeof(DUS_ENTRY)).

pRethExternalUsers  -  Pointer to the memory handle of an array of DUS_ENTRY structs returned to the caller.  The DUS allocates and assigns this handle, sets the user information into the array, and returns the handle UNLOCKED to the caller.  The array contains *pNumUsersReturned structs.  The caller will free the memory associated with the handle.

pRetUserEntrySize  -  Pointer to the size of the DUS_ENTRY struct.


**See Also :**
[DUS_ENTRY](/domino-c-api-docs/reference/Data/DUS_ENTRY)
---
