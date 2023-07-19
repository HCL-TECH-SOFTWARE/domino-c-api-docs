##### Data Type : DSAPI
##### FilterContext - DSAPI Filter context structure request information
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct _FilterContext {
   unsigned int   contextSize;
   unsigned int   revision;
   void*          serverContext;
   unsigned int   serverReserved;
   unsigned int   securePort;
   void*          privateContext;

   int (*GetRequest)(struct _FilterContext* pContext, 
                        FilterRequest* pRequest, 
                        unsigned int* pErrID);

   int (*GetRequestContents)(struct _FilterContext* pContext,
                        char** pContents, 
                        unsigned int* pErrID);

   int (*GetServerVariable)(struct _FilterContext* context, 
                        char* pName, 
                        void* pBuffer,
                        unsigned int bufferSize,
                        unsigned int* pErrID);

   int (*WriteClient)(struct _FilterContext* pContext, 
                        char* pBuffer,
                        unsigned int bufferLen,
                        unsigned int reserved,
                        unsigned int* pErrID);

   void* (*AllocMem)(struct _FilterContext* pContext, 
                        unsigned int size,
                        unsigned int reserved,
                        unsigned int* pErrID);

   int (*ServerSupport)(struct _FilterContext* pContext, 
                        unsigned int funcType,
                        void* pData1,
                        void* pData2,
                        unsigned int other,
                        unsigned int* pErrID);
} FilterContext;

**Description :**

The FilterContext structure contains information about the request, server call back functions, and a pointer to your own data.  This structure is needed to the entry point for which the filter is registered.  For example this entry point would be defined as follows:
<ul><br>
	<br>
	typedef unsigned int HttpFilterProc( FilterContext * pContext, unsigned int eventType, void* pEventData );<br>
<br>
The FilterContext structure:<br>
<br>
contextSize		- Input:		The size of the FilterContext structure.<br>
revision		- Input:		Same as FilterInitData serverFilterVersion.<br>
serverContext	- Input:		Pointer to the server'scontext.  This is for the server's use and should not be accessed by the filter library.<br>
serverReserved	- 		Reserved for future use.<br>
securePort		- Input:		The number 1 indicates the request came from HTTPS (SSL), 0 from HTTP<br>
privateContext	- Output:	Pointer for filter library's own data.<br>
<br>
<br>
<tt><font size="2">int (*GetRequest)(struct _FilterContext* pContext,FilterRequest* pRequest,unsigned int* pErrID);</font></tt><br>

<ul>The GetRequest callback allows the filter to gain access to the http request line. If successful, the http stack fills in the FilterRequest structure pointed to by pRequest with the http request URL, the user's name and his/her credentials (password or client certification), the request method, the http protocol used, and any post data. This callback function is always available to the filter since it is a member of the _FilterContext structure.<br>
Returns TRUE if successful, FALSE otherwise.<br>
<br>
pContext	- pointer to the structure FilterContext and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
pRequest	- pointer to an instance of the structure FilterRequest, to be filled in with the relevant information from the http request. see FilterRequest<br>
pErrID	- set to 0 if successful, to an error code otherwise.<br>
<br>
<br>
</ul>
<tt><font size="2">int (*GetRequestContents)(struct _FilterContext* pContext, char** pContents,unsigned int* pErrID);</font></tt>
<ul><br>
The GetRequestContents callback allows the filter to read any http post data.This callback function is always available to the filter since it is a member of the FilterContext structure.<br>
Returns the number of bytes read.<br>
<br>
pContext	- pointer to the structure FilterContext and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
pContents	- pointer to a pointer of type char, where the DSAPI layer will store the pointer to the buffer into wchich the post data has been read.<br>
pErrID	- set to 0 if successful, or to an error code otherwise. Possible error codes are DSAPI_INVALID_ARGUMENT, or DSAPI_MEMORY_ERROR.<br>
<br>
<br>
</ul>
<tt><font size="2">int (*GetServerVariable)(struct _FilterContext* pContext,char* pName,void* pBuffer,unsigned int bufferSize,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; unsigned int* pErrID);</font></tt>	<br>
	
<ul>The GetServerVariable callback allows the filter to access the value of either an http header or to a CGI environment variable. If the supplied buffer is too small to contains the result, it is still filled with the a partial result, and pErrID is set to DSAPI_BUFFER_TOO_SMALL. This callback function is always available to the filter since it is a member of the FilterContext structure.<br>
Return TRUE if successful, FALSE otherwise.<br>
<br>
pContext	- pointer to the structure _FilterContext and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
pName	- the name of the variable whose value is sought. This argument must be a valid pointer to a string.<br>
pBuffer	- buffer to return the value in. This argument cannot be NULL.<br>
bufferSize	- size in bytes of the supplied buffer.<br>
pErrID	- set to 0 if successful, or to an error code otherwise. Possible error codes are DSAPI_INVALID_ARGUMENT, DSAPI_BUFFER_TOO_SMALL.<br>
<br>

<ul></ul>
</ul>
<tt><font size="2">int (*WriteClient)(struct _FilterContext* pContext,char* pBuffer,unsigned int bufferLen,unsigned int reserved,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; unsigned int* pErrID);</font></tt>
<ul><br>
The WriteClient callback allows a filter to write response data directly to the client. Possible status codes are DSAPI_INVALID_ARGUMENT. This callback function is always available to the filter since it is a member of the FilterContext structure.<br>
Returns TRUE if successful, FALSE otherwise.<br>
<br>
pContext	- pointer to the structure FilterContext and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
pBuffer	- pointer to the buffer to write out. Cannot be NULL.<br>
bufferLen	- the number of bytes to write out.<br>
reserved	- reserved for future use.<br>
pErrID	-set to 0 if successful, to DSAPI_INVALID_ARGUMENT if pBuffer is NULL or if bufferLen is equal to zero.<br>
<br>
<br>
</ul>
<tt><font size="2">void* (*AllocMem)(struct _FilterContext* pContext,unsigned int size,unsigned int reserved,unsigned int* pErrID);</font></tt>
<ul><br>
The filter should use the AllocMem callback function to allocate dynamic memory. All memory allocated by AllocMem is automatically freed when the http stack thread finishes processing the http request. This simplifies your filter cleanup and ensures that the memory is freed even if the thread terminates abnormally. This callback function is always available to the filter since it is a member of the FilterContext structure.<br>
Returns a pointer to a block of memory if successful, NULL otherwise.<br>
<br>
pContext	- pointer to the structure FilterContext and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
size	- size in bytes of the block to allocate.<br>
reserved	- reserved for future use.<br>
pErrID	- set to 0 if successful, to DSAPI_MEMORY_ERROR otherwise.<br>
</ul>
</ul>
<br>

<ul><tt><font size="2">int (*ServerSupport)(struct _FilterContext* pContext,unsigned int funcType,void* pData1,void* pData2,</font></tt><br>
<tt><font size="2">		 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;unsigned int other,unsigned int* pErrID);</font></tt><br>

<ul>Filters use the ServerSupport callback to ask for a service to be performed on their behalf by the http stack. This callback function is always available to the filter since it is a member of the FilterContext structure.<br>
Returns TRUE if successful, FALSE otherwise.<br>
<br>
pContext	- (Input) pointer to the structure FilterContext.  Contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
funcType 	- type of service to be performed. see ServerSupportTypes<br>
pData1	- service-specific data pointer.  Format depends on which service is requested, as follows:
<ul>
<ul>
<ul>
<ul>
<ul>- pointer to a FilterResponseHeaders structure if funcType is kWriteResponseHeaders.  see FilterResponseHeaders<br>
- NULL if funcType is kOwnsRequest.<br>
- pointer to a FilterParsedRequestLine if funcType is kGetParsedRequest.  see FilterParsedRequestLine <br>
- pointer to a FilterAuthenticatedUser structure if funcType is kGetAuthenticatedUserInfo.  see FilterAuthenticatedUser </ul>
</ul>
</ul>
</ul>
</ul>
pData2	- not used <br>
other	- not used <br>
pErrID	- (Output) pointer to an integer where the server can store an error code</ul>
</ul>



**See Also :**
[FilterRequest](/domino-c-api-docs/reference/Data/FilterRequest)
[FilterResponseHeaders](/domino-c-api-docs/reference/Data/FilterResponseHeaders)
[RequestMethod](/domino-c-api-docs/reference/Data/RequestMethod)
[ServerSupportTypes](/domino-c-api-docs/reference/Data/ServerSupportTypes)
---
