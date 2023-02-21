##### Function : Domino Upgrade Services
##### DUSRetrieveGroupsEx - Returns information about the groups in a group or in a filter search result.
---
```
#include <dus.h>
STATUS LNCALLBACK DUSRetrieveGroupsEx(

	DHANDLE  hContext,
	char *pFilter,
	char *GroupName,
	NOTEHANDLE  hGroupNote,
	DWORD  StartIndex,
	DWORD *pResumeIndex,
	DWORD  NumGroupsRequested,
	DWORD *pNumGroupsReturned,
	DHANDLE *pRethExternalGroups,
	DWORD *pRetGroupEntrySize);
```
**Description :**

This function allocates and passes back an array of DUS_ENTRY structures 
containing information about the groups in a group or in a filter search 
result.  This function should continue to be called until the DUS returns a 
resume index of 0 or the *pNumGroupsReturned is less than 
*pNumGroupsRequested.  If group members are retrieved, calls will stop if 65K 
entries are retrieved.  If pFilter is NULL, and GroupName is valid, return 
members of a group.  If both are NULL, return all entries.

**Parameters :**
Input :
hContext  -  Handle to this DUS specific context information.

pFilter  -  Optional.  Filter string in application-defined format.

GroupName  -  Optional.  Name of group, non-NULL if members of the group are requested.

hGroupNote  -  Group note handle.

StartIndex  -  0L the first time DUS is called.  If all groups are not retrieved the first time and subsequent calls are necessary, this value is equal to the resume index passed back by the DUS on the previous call (*pResumeIndex).

NumGroupsRequested  -  Number of groups that should be provided to the caller, if available.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


pResumeIndex  -   Set this value if additional groups need to be returned to the DUS framework (number of available groups exceeds the number requested by the framework).  This value will be returned to the DUS on the subsequent DUSRetrieveGroups calls as the StartIndex.  When group retrieval is complete the pResumeIndex should be set to 0L.  The pResumeIndex will always be 0L the first time DUSRetrieveGroupsEx is called.

pNumGroupsReturned  -  Points to the number of groups returned by the DUS to the caller.  Groups are returned via the array of DUS_ENTRY structures represented by pRethExternalGroups.  This value should be used to allocate an array of DUS_ENTRY structures with the size:   NumGroupsRequested *  sizeof(DUS_ENTRY)).

pRethExternalGroups  -  Pointer to the memory handle  of an array of DUS_ENTRY structures returned to the caller.  The DUS allocates and assigns this handle, sets the user information into the array, and returns the handle UNLOCKED to the caller.  The array should contain *pNumUsersReturned structures.  The caller will free the memory associated with the handle.

pRetGroupEntrySize  -  Pointer to the size of the DUS_ENTRY structure.


**See Also :**
[DUSRetrieveGroups](/domino-c-api-docs/reference/Func/DUSRetrieveGroups)
---
