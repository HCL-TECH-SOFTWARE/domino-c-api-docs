##### Data Type : DSAPI
##### FilterResponse - Request response
---
```
#include <dsapi.h>
```

**Definition :**
```
typedef struct {
	unsigned int responseCode;
	char*   reasonText;

	int ( *GetAllHeaders )( FilterContext *pContext,
	      char **ppHeaders,
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
	     char *pHeader,
	     unsigned int *pErrID );

	unsigned int reserved;
	char*   userName;
} FilterResponse;
```

**Description :**

responseCode - Input parameter. It is the HTTP Response status code.
<ul>
<ul><br>
reasonText -<b> </b>Input parameter. It is the HTTP response status text if any.</ul>
</ul>

<ul>
<ul><b><i>int ( *GetAllHeaders )( FilterContext *pContext,</i></b><br>
<b><i>	char** ppHeaders,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
This callback function allows the filter to gain access to the response http headers.<br>
<br>
Returns the byte count of the buffer containing the http response headers.<br>
<br>
<i>pContext</i> is a pointer to the structure <i>FilterContext</i> and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
<i>ppHeaders</i> is a pointer to a location where the DSAPI layer will store the pointer to a buffer that will contain the response http headers.<br>
<br>
<i>pErrID</i> is a pointer to an unsigned integer that is set to 0 if successfull, to an error code otherwise. Possible error codes are: DSAPI_INVALID_ARGUMENT, DSAPI_MEMORY_ERROR and DSAPI_INTERNAL_ERROR.<br>
<br>
<b><i>int ( *GetHeader )( FilterContext *pContext,</i></b><br>
<b><i>	char *pName,</i></b><br>
<b><i>	char *pBuffer,</i></b><br>
<b><i>	unsigned int bufferSize,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
This callback function retreives a single http response header value. The http header name is supplied. If the http header does not exist, an empty string is returned in the supplied buffer.<br>
<br>
Returns 0 for for a hard failure (bad argument passed), the number of bytes valid in the buffer containing the result if successfull, or the required buffer size if the buffer is too small to contain the result.<br>
<br>
<i>pContext</i> is a pointer to the structure <i>FilterContext</i> and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
<i>pName </i>is a pointer to a string containing the name of the desired http header. This cannot be NULL or an empty string.<br>
<br>
<i>pBuffer</i> is a pointer to a buffer where to store the result. This argument cannot be NULL.<br>
<br>
<i>bufferSize</i> is the size of supplied buffer.<br>
<br>
<i>pErrID</i> is a pointer to an unsigned integer that is set to 0 if successfull, to DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the result.<br>
<br>
<b><i>int ( *SetHeader )( FilterContext *pContext,</i></b><br>
<b><i>	char *pName,</i></b><br>
<b><i>	char *pValue,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
This callback function allows a filter to change the value of an existing response http header. Note that if the http header does not exist, it is added to the list of http response headers.<br>
<br>
Returns TRUE if successfull, FALSE otherwise.<br>
<br>
<i>pContext</i> is a pointer to the structure <i>FilterContext</i> and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
<i>pName </i>is a pointer to a string containing the name of the http header to change. This argument cannot be NULL or an empty string.<br>
<br>
<i>pValue</i> is a pointer to a string containing the value for the http header.<br>
<br>
<i>pErrID</i> is a pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successfull, to a non zero value otherwise.<br>
<br>
<b><i>int ( *AddHeader )( FilterContext *pContext,</i></b><br>
<b><i>	char *pHheader,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
This callback function allows a filter to add an http header to the list of the response http headers. Note that if the http header already exists, its value is changed to reflect the new value.<br>
<br>
Return TRUE if successfull, FALSE otherwise.<br>
<br>
<i>pContext</i> is a pointer to the structure <i>FilterContext</i> and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
<i>pHeader</i> is a pointer to a valid http header. The expected format is the same as the format of response http headers, i.e., <i>&lt;headerName:value&gt;.</i><br>
<br>
<i>pErrID </i>is a pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successfull, to a non zero value otherwise. The only non zero in this case is DSAPI_INVALID_ARGUMENT which indicates that an error in the format of the supplied header has been detected.<br>
<br>
reserved <b><i>- </i></b>is reserved for future use.<br>
userName<b><i>- </i></b>Input parameter. The user's web name.</ul>
</ul>



**See Also :**
---
