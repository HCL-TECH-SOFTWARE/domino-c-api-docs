##### Data Type : DSAPI
##### FilterAuthenticate - DSAPI Filter authentication structure
---
##### #include <dsapi.h>
**Description :**
The FilterAuthenticate event occurs when the http stack is in the 
authentication phase of the process. The filter code can view the request and 
user credentials, authenticate the user for the http stack, or completly handle 
the request. pEventData is a pointer to an instance of the structure.

userName - (Input)  The user's web name from the input request. It is set to 
NULL if none is available.
password - (Input)  The user's web password from the input request. It is set 
to NULL if none is available.
clientCert - (Input)  The SSL client certification. It is set to NULL if none 
is available.
clientCertLen - (Input)  The length of the SSL client certificate. It is set to 
zero in none is available.
authFlags - (Input)  The authentication options that are enabled for the 
server. It can be one of more of the following "OR"ed together:  see 
FilterAuthConfigFlags
preAuthenticated - (Input)  Set to TRUE if the user has been already 
pre-authenticated presumably by a companion http stack (e.g., MS-IIS).
foundInCache - (Input)  Set to TRUE if the user is already cached in Domino's 
internal cache and will be authenticated on that basis unless the filter 
handles the event. This member allows filters not to re-authenticate an already 
authenticated user. Filters in this case should immediatly return 
kFilterNotHandled.
authNameSize - (Input)  The size of the buffer in which to store the 
authenticated user name. 
authName - (Input)  A pointer to a supplied buffer where the authenticated 
user's name (cannonical name) must be stored.
authType - (Output)  The filter, if it handles the event, must set this field 
to the type of authentication performed.  See FilterAuthenticationTypes
 

int ( *GetUserNameList )( FilterContext *pContext, LMBCS *pBuffer, unsigned int 
bufferSize, unsigned int *pNumNames, unsigned int reserved, unsigned int 
*pErrID );

The GetUserNameList callback function allows a filter to gain access to the 
user's group list.
Returns the number of bytes valid in the return buffer, -1 if the buffer is too 
small (the buffer is still filled to end). 

pContext - pointer to the structure _FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
pBuffer - pointer to a memory buffer where to return the user's group list 
after it has been computed. The format is a sequence of zero terminated 
strings, i.e, "<group1\0group2\0...groupn\0"
bufferSize - size of the memory block pointer to by pBuffer.
pNumNames - pointer where to store the number of names contained in the user's 
group name list.
reserved - reserved for future use. It should be set to 0.
pErrID - pointer to an unsigned integer where to store a status code. The 
status code is set to 0 if the operation is successful, to a non zero value 
otherwise. The only non zero in this case is DSAPI_INVALID_ARGUMENT which 
indicates that one or more of the supplied arguments is(are) not valid.

int ( *GetHeader )( FilterContext *pContext, char *pName, char *pBuffer, 
unsigned int bufferSize, unsigned int *pErrID );

The GetHeader callback function retreives a single http header value. The http 
header header name is supplied. If the http header does not exist, an empty 
string is returned in the supplied buffer.
Returns 0 for for a hard failure (bad argument passed), the number of bytes 
valid in the buffer containing the result if successful, or the required buffer 
size if the buffer is too small to contain the result.

pContext - pointer to the structure FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
pName - pointer to a string containing the name of the desired http header. 
This cannot be NULL or an empty string.
pBuffer - pointer to a buffer where to store the result. This argument cannot 
be NULL.
bufferSize - size of supplied buffer.
pErrID - pointer to an unsigned integer that is set to 0 if successful, to 
DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the 
result.

void ( *GetMappedResource )( FilterContext *pContext, char **ppBuffer, unsigned 
int *pErrID );

The GetMappedResource callback function retreives a mapped resource value. 

Returns 0 for for a hard failure (bad argument passed), the number of bytes 
valid in the buffer containing the result if successful, or the required buffer 
size if the buffer is too small to contain the result.

pContext - pointer to the structure FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
ppBuffer - pointer to a pointer to a buffer where to store the result. This 
argument cannot be NULL.
pErrID - pointer to an unsigned integer that is set to 0 if successful, to 
DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the 
result.


**See Also :**
[EventFlags](D:/md_files/EventFlags.md)
[FilterAuthConfigFlags](D:/md_files/FilterAuthConfigFlags.md)
[FilterAuthenticationTypes](D:/md_files/FilterAuthenticationTypes.md)
[FilterContext](D:/md_files/FilterContext.md)
[FilterInitData](D:/md_files/FilterInitData.md)
---
