##### Function : Domino Upgrade Services
##### DUSRetrieveGroups - Retrieve Groups within an array of DUS_ENTRY structs, for upgrade/migration.
---
##### #include <dus.h>
STATUS LNCALLBACK **DUSRetrieveGroups(**

	DHANDLE  hContext,
	DWORD  StartIndex,
	DWORD *pResumeIndex,
	DWORD  NumGroupsRequested,
	DWORD *pNumGroupsReturned,
	DHANDLE *pRethExternalGroups,
	DWORD *pRetGroupEntrySize);
**Description :**
This function allocates and passes back an array of DUS_ENTRY structs 
containing information about the users available for upgrade/migration.  
DUSRetrieveGroups() will continue to be called by the DUS framework until the 
DUS returns a resume index of 0 or the *pNumGroupsReturned is less than 
*pnumGroupsRequested.
**Parameters :**
Input :
hContext  -  handle to this DUS' specific context information.

StartIndex  -  set to 0L the first time DUS is called.  If all groups are not retrieved the first time and subsequent calls are necessary, this value is equal to the resume index passed back by the DUS on the previous call.

NumGroupsRequested  -  number of groups that should be provided to the caller.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


pResumeIndex  -  Set this value if additional groups need to be returned to the DUS framework.  This value will be returned to the DUS on the subsequent DUSRetrieveGroups calls as the StartIndex.  When group retrieval is complete the pResumeIndex should be set to 0L.  The pResumeIndex will always be 0L the first time DUSretrieveGroups is called.

pNumGroupsReturned  -  points to the number of groups returned by the DUS to the caller.  This value should be used to allocate an array of DUS_ENTRY structs with the size (NumGroupsRequested *  sizeof(DUS_ENTRY)).

pRethExternalGroups  -  pointer to the memory handle of an array of DUS_ENTRY structs returned to the caller.  The DUS allocates and assigns this handle, sets the user information into the array, and returns the handle UNLOCKED to the caller.  The array should contain *pNumUsersReturned structs.  The caller will free the memory associated with the handle.

pRetGroupEntrySize  -  pointer to the size of the DUS_ENTRY struct.

**See Also :**
[DUS_ENTRY](D:/md_files/DUS_ENTRY.md)
---
