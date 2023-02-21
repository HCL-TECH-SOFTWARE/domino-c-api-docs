##### Data Type : DSAPI
##### FilterContext - DSAPI Filter context structure request information
---
```
#include <dsapi.h>
```
**Description :**

The FilterContext structure contains information about the request, server call 
back functions, and a pointer to your own data.  This structure is needed to 
the entry point for which the filter is registered.  For example this entry 
point would be defined as follows:
	
	typedef unsigned int HttpFilterProc( FilterContext * pContext, unsigned 
int eventType, void* pEventData );

The FilterContext structure:

contextSize  - Input:  The size of the FilterContext structure.
revision  - Input:  Same as FilterInitData serverFilterVersion.
serverContext - Input:  Pointer to the server'scontext.  This is for the 
server's use and should not be accessed by the filter library.
serverReserved -   Reserved for future use.
securePort  - Input:  The number 1 indicates the request came from HTTPS (SSL), 
0 from HTTP
privateContext - Output: Pointer for filter library's own data.


int (*GetRequest)(struct _FilterContext* pContext,FilterRequest* 
pRequest,unsigned int* pErrID);

The GetRequest callback allows the filter to gain access to the http request 
line. If successful, the http stack fills in the FilterRequest structure 
pointed to by pRequest with the http request URL, the user's name and his/her 
credentials (password or client certification), the request method, the http 
protocol used, and any post data. This callback function is always available to 
the filter since it is a member of the _FilterContext structure.
Returns TRUE if successful, FALSE otherwise.

pContext - pointer to the structure FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
pRequest - pointer to an instance of the structure FilterRequest, to be filled 
in with the relevant information from the http request. see FilterRequest
pErrID - set to 0 if successful, to an error code otherwise.



int (*GetRequestContents)(struct _FilterContext* pContext, char** 
pContents,unsigned int* pErrID);

The GetRequestContents callback allows the filter to read any http post 
data.This callback function is always available to the filter since it is a 
member of the FilterContext structure.
Returns the number of bytes read.

pContext - pointer to the structure FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
pContents - pointer to a pointer of type char, where the DSAPI layer will store 
the pointer to the buffer into wchich the post data has been read.
pErrID - set to 0 if successful, or to an error code otherwise. Possible error 
codes are DSAPI_INVALID_ARGUMENT, or DSAPI_MEMORY_ERROR.



int (*GetServerVariable)(struct _FilterContext* pContext,char* pName,void* 
pBuffer,unsigned int bufferSize,
                        unsigned int* pErrID); 
	
The GetServerVariable callback allows the filter to access the value of either 
an http header or to a CGI environment variable. If the supplied buffer is too 
small to contains the result, it is still filled with the a partial result, and 
pErrID is set to DSAPI_BUFFER_TOO_SMALL. This callback function is always 
available to the filter since it is a member of the FilterContext structure.
Return TRUE if successful, FALSE otherwise.

pContext - pointer to the structure _FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
pName - the name of the variable whose value is sought. This argument must be a 
valid pointer to a string.
pBuffer - buffer to return the value in. This argument cannot be NULL.
bufferSize - size in bytes of the supplied buffer.
pErrID - set to 0 if successful, or to an error code otherwise. Possible error 
codes are DSAPI_INVALID_ARGUMENT, DSAPI_BUFFER_TOO_SMALL.



int (*WriteClient)(struct _FilterContext* pContext,char* pBuffer,unsigned int 
bufferLen,unsigned int reserved,
                        unsigned int* pErrID);

The WriteClient callback allows a filter to write response data directly to the 
client. Possible status codes are DSAPI_INVALID_ARGUMENT. This callback 
function is always available to the filter since it is a member of the 
FilterContext structure.
Returns TRUE if successful, FALSE otherwise.

pContext - pointer to the structure FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
pBuffer - pointer to the buffer to write out. Cannot be NULL.
bufferLen - the number of bytes to write out.
reserved - reserved for future use.
pErrID -set to 0 if successful, to DSAPI_INVALID_ARGUMENT if pBuffer is NULL or 
if bufferLen is equal to zero.



void* (*AllocMem)(struct _FilterContext* pContext,unsigned int size,unsigned 
int reserved,unsigned int* pErrID);

The filter should use the AllocMem callback function to allocate dynamic 
memory. All memory allocated by AllocMem is automatically freed when the http 
stack thread finishes processing the http request. This simplifies your filter 
cleanup and ensures that the memory is freed even if the thread terminates 
abnormally. This callback function is always available to the filter since it 
is a member of the FilterContext structure.
Returns a pointer to a block of memory if successful, NULL otherwise.

pContext - pointer to the structure FilterContext and contains all the context 
data needed by the DSAPI layer implementation to identify which request this 
pertains to.
size - size in bytes of the block to allocate.
reserved - reserved for future use.
pErrID - set to 0 if successful, to DSAPI_MEMORY_ERROR otherwise.



int (*ServerSupport)(struct _FilterContext* pContext,unsigned int 
funcType,void* pData1,void* pData2,
	             unsigned int other,unsigned int* pErrID);

Filters use the ServerSupport callback to ask for a service to be performed on 
their behalf by the http stack. This callback function is always available to 
the filter since it is a member of the FilterContext structure.
Returns TRUE if successful, FALSE otherwise.

pContext - (Input) pointer to the structure FilterContext.  Contains all the 
context data needed by the DSAPI layer implementation to identify which request 
this pertains to.
funcType  - type of service to be performed. see ServerSupportTypes
pData1 - service-specific data pointer.  Format depends on which service is 
requested, as follows:
- pointer to a FilterResponseHeaders structure if funcType is 
kWriteResponseHeaders.  see FilterResponseHeaders
- NULL if funcType is kOwnsRequest.
- pointer to a FilterParsedRequestLine if funcType is kGetParsedRequest.  see 
FilterParsedRequestLine 
- pointer to a FilterAuthenticatedUser structure if funcType is 
kGetAuthenticatedUserInfo.  see FilterAuthenticatedUser 
pData2 - not used 
other - not used 
pErrID - (Output) pointer to an integer where the server can store an error code


**See Also :**
[FilterRequest](/domino-c-api-docs/reference/Data/FilterRequest)
[FilterResponseHeaders](/domino-c-api-docs/reference/Data/FilterResponseHeaders)
[RequestMethod](/domino-c-api-docs/reference/Data/RequestMethod)
[ServerSupportTypes](/domino-c-api-docs/reference/Data/ServerSupportTypes)
---
