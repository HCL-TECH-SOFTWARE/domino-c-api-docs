##### Data Type : DSAPI
##### FilterRawRequest - Filter raw request (headers not processed yet)
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct {
	unsigned int requestMethod;

	int ( *GetAllHeaders )( FilterContext *pContext,
	      char** ppHeaders,
	      unsigned int *pErrID );

	int ( *GetHeader )( FilterContext *pContext,
	     char *pName,
	     char *pBuffer,
	     unsigned int bufferSize,
	     unsigned int *pErrID );

	int ( *SetHeader )( FilterContext *pContext,
	     char *pName,
	     char *pValue,
	     unsigned int *pErrID );

	int ( *AddHeader )( FilterContext *pContext,
	     char *pHheader,
	     unsigned int *pErrID );

	unsigned int reserved;
} FilterRawRequest;

**Description :**


<ul>
<ul>requestMethod<i>- </i>is the request method. It can be one of the following:
<ul>
<ul>	kRequestNone: 	No HTTP request method is provided.<br>
	kRequestHEAD:	Method is often used for testing hypertext links for validity, accessibility, and recent modification.<br>
	kRequestGET: 	GET method - used to retrieve whatever information (in the form of an entity) is identified by the Request-URL.<br>
	kRequestPOST: 	POST method - requests that the origin server accept the entity enclosed in the request as a new subordinate of the resource identified by the Request-URL in the Request-Line.<br>
	kRequestPUT: 	PUT method - requests that the enclosed entity be stored under the supplied Request-URL.<br>
	kRequestDELETE:	DELETE method - requests that the origin server delete the resource identified by the Request-URL.<br>
	kRequestTRACE:	TRACE method.<br>
	kRequestCONNECT:	CONNECT method.<br>
	kRequestOPTIONS:	OPTIONS method.<br>
	kRequestUNKNOWN: 	Unknown request method.<br>
	kRequestBAD: 	Bad request method. Error.<br>
</ul>
</ul>
<b>int ( *GetAllHeaders )( FilterContext *pContext,</b><br>
<b>	char** ppHeaders,</b><br>
<b>	unsigned int *pErrID );</b>
<ul>This callback function allows the filter to gain access to the input http headers.<br>
<br>
Returns the byte count of the buffer containing the http headers.<br>
<br>
pContext is a pointer to the structure, FilterContext, and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
ppHeaders is a pointer to a location where the DSAPI layer will store the pointer to a buffer that will contain the input http headers. The format for the http headers is the following: &quot;&lt;header1&gt;&lt;\r\n&gt;&lt;header2&gt;&lt;\r\n&gt;....&lt;headern&gt;&lt;\r\n&gt;&lt;\r\n&gt;&quot;.<br>
<br>
pErrID is a pointer to an unsigned integer that is set to 0 if successful, to an error code otherwise. Possible error codes are: DSAPI_INVALID_ARGUMENT, DSAPI_MEMORY_ERROR and DSAPI_INTERNAL_ERROR.</ul>
<br>
<b>int ( *GetHeader )( FilterContext *pContext,</b><br>
<b>	char *pName,</b><br>
<b>	char *pBuffer,</b><br>
<b>	unsigned int bufferSize,</b><br>
<b>	unsigned int *pErrID );</b>
<ul>This callback function retrieves a single http header value. The http header name is supplied. If the http header does not exist, an empty string is returned in the supplied buffer.<br>
<br>
Returns 0 for a hard failure (bad argument passed), the number of bytes valid in the buffer containing the result if successful, or the required buffer size if the buffer is too small to contain the result.<br>
<br>
pContext is a pointer to the structure, FilterContext, and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
pName is a pointer to a string containing the name of the desired http header. This cannot be NULL or an empty string.<br>
<br>
pBuffer is a pointer to a buffer where to store the result. This argument cannot be NULL.<br>
<br>
bufferSize is the size of supplied buffer.<br>
<br>
pErrID is a pointer to an unsigned integer that is set to 0 if successful, to DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the result.<br>
</ul>
<b>int ( *SetHeader )( FilterContext *pContext,</b><br>
<b>	char *pName,</b><br>
<b>	char *pValue,</b><br>
<b>	unsigned int *pErrID );</b>
<ul>This callback function allows a filter to change the value of an existing input http header. Note that if the http header does not exist, it is added to the list of input headers.<br>
<br>
Returns TRUE if successful, FALSE otherwise.<br>
<br>
pContext is a pointer to the structure, FilterContext, and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
pName is a pointer to a string containing the name of the http header to change. This argument cannot be NULL or an empty string.<br>
<br>
pValue is a pointer to a string containing the value for the http header.<br>
<br>
pErrID is a pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successful, to a non-zero value otherwise.</ul>
<br>
<b>int ( *AddHeader )( FilterContext *pContext,</b><br>
<b>	char *pHheader,</b><br>
<b>	unsigned int *pErrID );</b>
<ul>This callback function allows a filter to add an http header to the list of the input http headers. Note that if the http header already exists, its value is changed to reflect the new value.<br>
<br>
Return TRUE if successful, FALSE otherwise.<br>
<br>
pContext is a pointer to the structure, FilterContext, and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
pHeader is a pointer to a valid http header. The expected format is the same as the format of input http headers, i.e., <i>&lt;headerName:value&gt;.</i><br>
<br>
pErrID<i> </i>is a pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successful, to a non-zero value otherwise. The only valid non-zero status in this case is DSAPI_INVALID_ARGUMENT which indicates that an error in the format of the supplied header has been detected.</ul>
<br>
 reserved<b> </b>- is reserved for future use.</ul>
</ul>



**See Also :**
---
