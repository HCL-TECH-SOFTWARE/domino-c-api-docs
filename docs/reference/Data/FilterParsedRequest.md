##### Data Type : DSAPI
##### FilterParsedRequest - Filter parsed request
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct {
	unsigned int requestMethod;

	int ( *GetAllHeaders )( FilterContext *pContext,
	      char **ppHeaders,
	      unsigned int *pErrID );

	int ( *GetHeader )( FilterContext *pContext,
	     char *pName,
	     char *pBuffer,
	     unsigned int bufferSize,
	     unsigned int *pErrID );

	unsigned int reserved;
} FilterParsedRequest;

**Description :**

After pre-parsing of the http input headers, this structure could be utilized to process a request again ( only access the headers, not change the headers ). 
<ul>
<ul><br>
int ( *GetAllHeaders )( FilterContext *pContext,<br>
	char** ppHeaders,<br>
	unsigned int *pErrID );<br>

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
<br>
int ( *GetHeader )( FilterContext *pContext,<br>
	char *pName,<br>
	char *pBuffer,<br>
	unsigned int bufferSize,<br>
	unsigned int *pErrID );
<ul><br>
This callback function retrieves a single http header value. The http header name is supplied. If the http header does not exist, an empty string is returned in the supplied buffer.<br>
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
pErrID is a pointer to an unsigned integer that is set to 0 if successful, to DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the result.</ul>
</ul>
</ul>



**See Also :**
---
