##### Data Type : DSAPI
##### FilterUserNameList - DSAPI Filter User Name List Event Structure
---
```
#include <dsapi.h>
```
**Description :**

The FilterUserNameList event occurs when the http stack is about to generate 
the user's group name list. These are group names the user is a member of. This 
event follows the kFilterAuthenticate event. The filter can have the Domino 
server populate the list, add or remove groups to/from the list or completly 
handle the event (generate completly the group list itself). The parameter in 
the function HttpEventProc pEventData is a pointer to the structure 
FilterUserNameList.

userName: the authenticated user name.

int ( *GetUserNameList )( FilterContext *pContext, LMBCS *pBuffer, unsigned int 
bufferSize, unsigned int *pNumNames, unsigned int reserved, unsigned int 
*pErrID );
The GetUserNameList callback function allows a filter to gain access to the 
user's group list.
Returns the number of bytes valid in the supplied buffer, (-1) if the buffer is 
too small (although the buffer is filled to end).

pContext  - pointer to the structure _FilterContext and contains all the 
context data needed by the DSAPI layer implementation to identify which request 
this pertains to.
pBuffer  - pointer to a memory buffer where to return the user's group list 
after it has been computed. The format is sequence of zero terminated strings, 
i.e., "<group1\0group2\n...groupn\0>".
bufferSize - size of the memory block pointer to by pBuffer.
pNumNames - pointer where to store the number of names contained in the user's 
group list.
reserved - reserved for future use. It should be set to 0.
pErrID - pointer to an unsigned integer where to store a status code. The 
status code is set to 0 if the operation is successful, to a non zero value 
otherwise. The only non zero in this case is DSAPI_INVALID_ARGUMENT which 
indicates that one or more of the supplied arguments is(are) not valid.

int ( *PopulateUserNameList )( FilterContext *pContext, LMBCS *pBuffer, 
unsigned int bufferSize, unsigned int *pNumNames, unsigned int reserved, 
unsigned int *pErrID );
The PopulateUserNameList callback function allows a filter to request that the 
user's group list be computed and returned in the supplied buffer.
Returns the number of valid bytes returned in pBuffer.

pContext - pointer to the structure _FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
pBuffer - pointer to a memory buffer where to return the user's group list 
after it has been computed.
bufferSize - size of the memory block pointer to by pBuffer.
pNumNames - pointer where to store the number of names contained in the user's 
group list.
reserved - reserved for future use. It should be set to 0.
pErrID - pointer to an unsigned integer where to store a status code. The 
status code is set to 0 if the operation is successful, to a non zero value 
otherwise.

int ( *AddGroupsToList )( FilterContext *pCcontext, LMBCS *pGroupNames, 
unsigned int numGroupNames, unsigned int reserved, unsigned int *pErrID );
The AddGroupsToList callback function allows the filter to dynamically augment 
the user's group.
Returns TRUE if successful, FALSE otherwise

pContext - pointer to the structure _FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
pBuffer - pointer to a buffer that contains the names to add to the user's 
group list. The format is a list of strings each of which contains the group 
name, i.e., < string1 string2 ... stringn >. Strings here are defined as C 
strings, i.e., a 0 terminated sequence of bytes.
numGroupName - the number of group names contained in the pBuffer.
reserved - reserved for future use. It should be set to 0.
pErrID - pointer to an unsigned integer where to store a status code. The 
status code is set to 0 if the operation is successful, to a non zero value 
otherwise. In this case it is always set to 0.

int ( *RemoveGroupsFromList )( FilterContext *pContext, unsigned int reserved, 
unsigned int *pErrID);
The RemoveGroupsFromList callback allows the filter to clear the user's group 
list. The result would a group list that contains only the user's known names.
Returns TRUE

pContext - pointer to the structure _FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
reserved - reserved and should be always set to 0.
pErrID - pointer to an unsigned integer where to store a status code. The 
status code is always set to 0.

reserved - is reserved for future use.

Note that the altered group names list is not seen by the current 
implementation of Domino's agents (agents compute their own group names list 
based on the authenticated user name).


**See Also :**
[FilterContext](/domino-c-api-docs/reference/Data/FilterContext)
[FilterInitData](/domino-c-api-docs/reference/Data/FilterInitData)
---
