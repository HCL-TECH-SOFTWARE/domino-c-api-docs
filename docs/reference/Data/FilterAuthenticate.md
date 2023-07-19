##### Data Type : DSAPI
##### FilterAuthenticate - DSAPI Filter authentication structure
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct {
	LMBCS*   userName;
	LMBCS*   password;
	unsigned char* clientCert;
	unsigned int clientCertLen;
	unsigned int authFlags;
	unsigned int preAuthenticated;
	unsigned int foundInCache;
	unsigned int authNameSize;
	LMBCS*   authName;
	unsigned int authType;

	int ( *GetUserNameList )( FilterContext *pContext, 
	     LMBCS *pBuffer,
	     unsigned int bufferSize,
	     unsigned int *pNumNames,
	     unsigned int reserved,
	     unsigned int *pErrID );

	int ( *GetHeader )( FilterContext *pContext,
	     char *pName,
	     char *pBuffer,
	     unsigned int bufferSize,
	     unsigned int *pErrID );

	void ( *GetMappedResource )( FilterContext *pContext,
	     char **ppBuffer,
	     unsigned int *pErrID );

} FilterAuthenticate;

**Description :**

The FilterAuthenticate event occurs when the http stack is in the authentication phase of the process. The filter code can view the request and user credentials, authenticate the user for the http stack, or completly handle the request. pEventData is a pointer to an instance of the structure.<br>

<ul>userName	- (Input)  The user's web name from the input request. It is set to NULL if none is available.<br>
password	- (Input)  The user's web password from the input request. It is set to NULL if none is available.<br>
clientCert	- (Input)  The SSL client certification. It is set to NULL if none is available.<br>
clientCertLen	- (Input)  The length of the SSL client certificate. It is set to zero in none is available.<br>
authFlags	- (Input)  The authentication options that are enabled for the server. It can be one of more of the following &quot;OR&quot;ed together:  see FilterAuthConfigFlags<br>
preAuthenticated	- (Input)  Set to TRUE if the user has been already pre-authenticated presumably by a companion http stack (e.g., MS-IIS).<br>
foundInCache	- (Input)  Set to TRUE if the user is already cached in Domino's internal cache and will be authenticated on that basis unless the filter handles the event. This member allows filters not to re-authenticate an already authenticated user. Filters in this case should immediatly return kFilterNotHandled.<br>
authNameSize	- (Input)  The size of the buffer in which to store the authenticated user name. <br>
authName	- (Input)  A pointer to a supplied buffer where the authenticated user's name (cannonical name) must be stored.<br>
authType	- (Output)  The filter, if it handles the event, must set this field to the type of authentication performed.  See FilterAuthenticationTypes<br>
 <br>
<br>
<tt><font size="2">int ( *GetUserNameList )( FilterContext *pContext, LMBCS *pBuffer, unsigned int bufferSize, unsigned int *pNumNames, unsigned int reserved, unsigned int *pErrID );</font></tt>
<ul><br>
The GetUserNameList callback function allows a filter to gain access to the user's group list.<br>
Returns the number of bytes valid in the return buffer, -1 if the buffer is too small (the buffer is still filled to end). <br>
<br>
pContext	- pointer to the structure _FilterContext and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
pBuffer	- pointer to a memory buffer where to return the user's group list after it has been computed. The format is a sequence of zero terminated strings, i.e, &quot;&lt;group1\0group2\0...groupn\0&quot;<br>
bufferSize	- size of the memory block pointer to by pBuffer.<br>
pNumNames	- pointer where to store the number of names contained in the user's group name list.<br>
reserved	- reserved for future use. It should be set to 0.<br>
pErrID	- pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successful, to a non zero value otherwise. The only non zero in this case is DSAPI_INVALID_ARGUMENT which indicates that one or more of the supplied arguments is(are) not valid.<br>
</ul>
<tt><font size="2">int ( *GetHeader )( FilterContext *pContext, char *pName, char *pBuffer, unsigned int bufferSize, unsigned int *pErrID );</font></tt><br>

<ul>The GetHeader callback function retreives a single http header value. The http header header name is supplied. If the http header does not exist, an empty string is returned in the supplied buffer.<br>
Returns 0 for for a hard failure (bad argument passed), the number of bytes valid in the buffer containing the result if successful, or the required buffer size if the buffer is too small to contain the result.<br>
<br>
pContext	- pointer to the structure FilterContext and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
pName	- pointer to a string containing the name of the desired http header. This cannot be NULL or an empty string.<br>
pBuffer	- pointer to a buffer where to store the result. This argument cannot be NULL.<br>
bufferSize	- size of supplied buffer.<br>
pErrID	- pointer to an unsigned integer that is set to 0 if successful, to DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the result.<br>
</ul>
<tt><font size="2">void ( *GetMappedResource )( FilterContext *pContext, char **ppBuffer, unsigned int *pErrID );</font></tt><br>

<ul>The GetMappedResource callback function retreives a mapped resource value. <br>
<br>
Returns 0 for for a hard failure (bad argument passed), the number of bytes valid in the buffer containing the result if successful, or the required buffer size if the buffer is too small to contain the result.<br>
<br>
pContext	- pointer to the structure FilterContext and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
ppBuffer	- pointer to a pointer to a buffer where to store the result. This argument cannot be NULL.<br>
pErrID	- pointer to an unsigned integer that is set to 0 if successful, to DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the result.<br>
</ul>
</ul>



**See Also :**
[EventFlags](/domino-c-api-docs/reference/Data/EventFlags)
[FilterAuthConfigFlags](/domino-c-api-docs/reference/Data/FilterAuthConfigFlags)
[FilterAuthenticationTypes](/domino-c-api-docs/reference/Data/FilterAuthenticationTypes)
[FilterContext](/domino-c-api-docs/reference/Data/FilterContext)
[FilterInitData](/domino-c-api-docs/reference/Data/FilterInitData)
---
