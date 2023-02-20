##### Data Type : DSAPI
##### FilterResponse - Request response
---
```
#include <dsapi.h>
```
**Description :**

responseCode - Input parameter. It is the HTTP Response status code.

reasonText - Input parameter. It is the HTTP response status text if any.

int ( *GetAllHeaders )( FilterContext *pContext,
	char** ppHeaders,
	unsigned int *pErrID );
This callback function allows the filter to gain access to the response http 
headers.

Returns the byte count of the buffer containing the http response headers.

pContext is a pointer to the structure FilterContext and contains all the 
context data needed by the DSAPI layer implementation to identify which request 
this pertains to.

ppHeaders is a pointer to a location where the DSAPI layer will store the 
pointer to a buffer that will contain the response http headers.

pErrID is a pointer to an unsigned integer that is set to 0 if successfull, to 
an error code otherwise. Possible error codes are: DSAPI_INVALID_ARGUMENT, 
DSAPI_MEMORY_ERROR and DSAPI_INTERNAL_ERROR.

int ( *GetHeader )( FilterContext *pContext,
	char *pName,
	char *pBuffer,
	unsigned int bufferSize,
	unsigned int *pErrID );
This callback function retreives a single http response header value. The http 
header name is supplied. If the http header does not exist, an empty string is 
returned in the supplied buffer.

Returns 0 for for a hard failure (bad argument passed), the number of bytes 
valid in the buffer containing the result if successfull, or the required 
buffer size if the buffer is too small to contain the result.

pContext is a pointer to the structure FilterContext and contains all the 
context data needed by the DSAPI layer implementation to identify which request 
this pertains to.

pName is a pointer to a string containing the name of the desired http header. 
This cannot be NULL or an empty string.

pBuffer is a pointer to a buffer where to store the result. This argument 
cannot be NULL.

bufferSize is the size of supplied buffer.

pErrID is a pointer to an unsigned integer that is set to 0 if successfull, to 
DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the 
result.

int ( *SetHeader )( FilterContext *pContext,
	char *pName,
	char *pValue,
	unsigned int *pErrID );
This callback function allows a filter to change the value of an existing 
response http header. Note that if the http header does not exist, it is added 
to the list of http response headers.

Returns TRUE if successfull, FALSE otherwise.

pContext is a pointer to the structure FilterContext and contains all the 
context data needed by the DSAPI layer implementation to identify which request 
this pertains to.

pName is a pointer to a string containing the name of the http header to 
change. This argument cannot be NULL or an empty string.

pValue is a pointer to a string containing the value for the http header.

pErrID is a pointer to an unsigned integer where to store a status code. The 
status code is set to 0 if the operation is successfull, to a non zero value 
otherwise.

int ( *AddHeader )( FilterContext *pContext,
	char *pHheader,
	unsigned int *pErrID );
This callback function allows a filter to add an http header to the list of the 
response http headers. Note that if the http header already exists, its value 
is changed to reflect the new value.

Return TRUE if successfull, FALSE otherwise.

pContext is a pointer to the structure FilterContext and contains all the 
context data needed by the DSAPI layer implementation to identify which request 
this pertains to.

pHeader is a pointer to a valid http header. The expected format is the same as 
the format of response http headers, i.e., <headerName:value>.

pErrID is a pointer to an unsigned integer where to store a status code. The 
status code is set to 0 if the operation is successfull, to a non zero value 
otherwise. The only non zero in this case is DSAPI_INVALID_ARGUMENT which 
indicates that an error in the format of the supplied header has been detected.

reserved - is reserved for future use.
userName- Input parameter. The user's web name.

**See Also :**
---
