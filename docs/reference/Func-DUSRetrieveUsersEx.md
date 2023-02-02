##### Function : Domino Upgrade Services
##### DUSRetrieveUsersEx - Retrieve information about users in a group or in a filter search result.
---
##### #include <dus.h>
STATUS LNCALLBACK **DUSRetrieveUsersEx(**

	DHANDLE  hContext,
	char *Filter,
	char *GroupName,
	NOTEHANDLE  hGroupNote,
	DWORD  StartIndex,
	DWORD *pResumeIndex,
	DWORD  NumUsersRequested,
	DWORD *pNumUsersReturned,
	DHANDLE *pRethExternalUsers,
	DWORD *pRetUserEntrySize);
**Description :**
This function allocates and passes back an array of DUS_ENTRY structures 
containing information about the users in a group or in a filter search 
result.  This function should continue to be called until the DUS returns a 
resume index of 0 or the *pNumUsersReturned is less than *pNumUsersRequested.  
If group members are retrieved, calls will stop if 65K entries are retrieved.  
If pFilter is NULL, and GroupName is valid, return members of a group.  If both 
are NULL, return all entries.
**Parameters :**
Input :
hContext  -  This is a handle to this DUS' specific context information. It's provided by the DUS with DUSStart and passed back with every call by the DUS framework.

Filter  -  Optional.  This is a filter string in an application-defined format that the user has selected.

GroupName  -  Optional.  Name of group, non-NULL if members of the group are requested.

hGroupNote  -  Group note handle.

StartIndex  -  Set this value to 0L the first time the DUS is called.  If all users are not retrieved, the first time and subsequent calls are necessary. This value is equal to the resume index passed back by the DUS on the previous call (*pResumeIndex).

NumUsersRequested  -  The number of users that should be provided to the caller, if available.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


pResumeIndex  -  Set this value if additional users need to be returned to the DUS framework (number of available users exceeds the number requested by the framework).  This value will be returned to the DUS on the subsequent DUSRetrieveUsersEx call as the StartIndex.  When user retrieval is complete the pResumeIndex should be set to 0L.  The pResumeIndex will always be 0L the first time DUSRetrieveUsersEx is called.

pNumUsersReturned  -  Points to the number of users returned by the DUS to the caller.  Users are returned via the array of DUS_ENTRY structures represented by pRethExternalUsers.  This value should be used to allocate an array of DUS_ENTRY structures with the size:   NumUsersRequested *  sizeof(DUS_ENTRY)).

pRethExternalUsers  -  Pointer to the memory handle  of an array of DUS_ENTRY structures returned to the caller.  The DUS allocates and assigns this handle, sets the user information into the array, and returns the handle UNLOCKED to the caller.  The array should contain *pNumUsersReturned structures.  The caller will free the memory associated with the handle.

pRetUserEntrySize  -  Pointer to the size of the DUS_ENTRY structure. (an array of which are allocated by the DUS and passed back to the caller)

**See Also :**
[DUSRetrieveUsers](D:/md_files/DUSRetrieveUsers.md)
---
