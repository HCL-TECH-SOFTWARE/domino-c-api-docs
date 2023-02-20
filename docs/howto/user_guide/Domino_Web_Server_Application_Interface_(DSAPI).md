##### Chapter 9-11
##### Domino Web Server Application Interface (DSAPI)

<b><font size="5" color="#000080">Overview </font></b><br>
<br>
The Domino Web Server Application Programming Interface (DSAPI) is a C API that lets you write your own extensions to the Domino Web Server.  DSAPI extensions, or filters, are notified whenever a particular event occurs during the processing of an http request. <br>
<br>
A DSAPI filter allows you to customize the processing of an http request when particular events occur. The http stack notifies the filter(s) of the event.   There are currently 13 events that can be captured by a DSAPI filter.  Depending on the design and its implementation, a filter can support one or any number of events.<br>
<br>
The implementation of the DSAPI interface relies on the filter to indicate which of the events it supports. The filter then receives notifications only for those events it claims it supports.<br>
<br>
Please refer to the <i>HCL C API Reference</i> for further information on any of the filter data structures referred to in this document.<br>
<br>
<b><font size="5" color="#000080">Getting Started</font></b><br>
<br>
A DSAPI filter must specify two entry points:<br>

<ol type="1">
<li><font color="#000080">Initialization</font>
<li><font color="#000080">Event Notification</font></ol>
<br>
An optional entry point may be defined for <font color="#000080">filter termination</font>.  Also, optional entry points may be defined for thread initialization and termination.<br>
<br>
<b><u><font color="#000080">Initialization</font></u></b><br>
<u><font color="#000080">	</font></u><br>
Domino calls the Initialization function when the filter is loaded.  The filter is loaded when the Domino HTTP server task is started or when the HTTP task is restarted with the Domino console command, &quot;tell http restart&quot;.  The prototype of the Initialization function is:<br>
	/*---<br>
	*		filter initialization<br>
	*/<br>
	unsigned int FilterInit(FilterInitData* pFilterInitData);<br>
<br>
The name of the Initialization function must be FilterInit for the DSAPI layer to find it when it loads the filter.  <br>
<br>
Refer to the <i>HCL C API Reference </i>for further information on the FilterInitData structure. <br>
<br>
<b><u><font color="#000080">Event Notification</font></u></b><br>
<br>
The Event Notification function does the actual work of the filter. Domino calls the Event Notification function whenever a particular event occurs during the processing of an http request.  When Domino calls the filter's Event Notification function it passes information about the request and the event being processed. On each call the filter can decide to handle the event, with or without an error return, or decline to handle the event.  The prototype for the Event Notification function is:<br>
	/*---<br>
	*		filter notification handling<br>
	*/<br>
	unsigned int HttpFilterProc(FilterContext* pContext, unsigned int eventType, void* pEventData);<br>
<br>
The name of the event handling function must be HttpFilterProc for the DSAPI layer to find it when it loads the filter.<br>
<br>
<b>pContext</b> is a pointer to the FilterContext that contains information about the http request, server callback function pointers, and a pointer to the filter's own data context.  Refer to the <i>HCL C API Reference </i>for further information on the FilterContext structure. <br>
<br>
<b>eventType</b> indicates which event is occurring.<br>
<br>
<b>pEventData</b> is a pointer to a structure associated with the event. There is a different event data structure for each event.  See the Events section below for details.<br>
<br>
<br>
Optional <b><u><font color="#000080">Thread Initialization and Termination</font></u></b><br>
<br>
The filter may also define entry points for the initialization and termination of threads.  The http stack will call the function HttpFilterThreadInit after  calling the initialization function FilterInit. HttpFilterThreadInit is mostly used to initialize any thread locals.   The prototype of the Filter Thread Initialization function is:<br>
	<br>
	unsigned int HttpFilterThreadInit (int threadType);<br>
<br>
The Filter Thread Initialization function requires the Filter Thread Termination function.  This function will be called when the library is unloaded to allow the filter to deallocate any of the resources allocated by the Filter Thread Initialization function.  The prototype of the Filter Thread Termination function is:<br>
<br>
<b><i><font face="Courier New">	</font></i></b>unsigned int HttpFilterThreadTerm ( int threadType );<br>
<br>
Optional <b><u><font color="#000080">Termination</font></u></b><br>
<br>
The filter may also define a Termination entry point. Domino will call this function whenever the filter is about to be unloaded - when the http stack process is shutting down. The filter can use this function to clean up resources it allocated.  The filter must deallocate all global resources it allocated when its initialization routine was called.  The prototype of the Filter Termination function is:<br>
	/*---<br>
	*		filter termination<br>
	*/<br>
	unsigned int TerminateFilter(unsigned int reserved);<br>
<br>
All the exported functions return an unsigned int status code.  The possible values of the status code are as follows:<br>

<ul type="disc">
<li>kFilterHandledRequest signals that the http request has completely been processed. A response has already been sent to the client, and the http stack must terminate the processing of the request.
<li>kFilterHandledEvent signals that the event has been handled, but further processing is to take place to completely service the http request.
<li>kFilterNotHandled signals that the filter did not process the event.
<li>kFilterError signals that the filter encountered an error while processing the event.  In this case the http stack is to stop processing the request, and send an appropriate error response to the user.</ul>
<br>
Note that for the functions FilterInit, HttpFilterThreadInit, HttpFilterThreadTerm, and TerminateFilter, the only possible return codes are kFilterHandledEvent and kFilterError. The function HttpFilterProc can return any of the status codes when handling an event.<br>
<br>
<b><font size="5" color="#000080">Events</font></b><br>
<br>
Events occur in a specific sequence.  They reflect the state of the http stack at each of its processing steps.  Event notifications can be seen as an opportunity for a filter(s) to override the default implementation of a given processing step.  With each event, a structure, which contains additional information and in most cases additional callback functions, is passed to the filter's event notification handling routine.  The filter can call the callback functions to get additional information or to have a service performed.  The event notification routine is only called for those events the filter is registered for (those that were passed in the FilterInitData structure when the filter was loaded and initialized).  Events are described below in the sequence in which they happen.<br>
<br>
<b>kFilterStartRequest Event</b><br>
This event is used to advise all filters currently loaded that an http request has been received, and is about to be processed. A filter, in this step, can prepare itself for processing the request. Typically in this step, the filters should allocate its own private context data, and required resources necessary to handle the processing of a request. The argument, pEventData, is not used and a NULL is passed.  Any filter supporting this event should return the value, kFilterHandledEvent.<br>
<br>
<b>kFilterRawRequest Event</b><br>
All filters currently loaded and supporting this event are notified that all the input http headers have been read in.  Any filter that needs to preprocess the input headers can do so at this time. Note that a filter could choose to completely service the http request at this time. The argument, pEventData, is a pointer to the FilterRawRequest structure. The structure FilterRawRequest is described below:<br>

<ul>
<ul><b>typedef struct {</b></ul>
</ul>
<b><font size="4">	</font></b><b>	unsigned int requestMethod;</b>
<ul>
<ul><br>
<b>	int ( *GetAllHeaders )( FilterContext *pContext,</b><br>
<b>					char** ppHeaders,</b><br>
<b>					unsigned int *pErrID );</b><br>
<br>
<b>	int ( *GetHeader )( FilterContext *pContext,</b><br>
<b>	char *pName,</b><br>
<b>	char *pBuffer,</b><br>
<b>	unsigned int bufferSize,</b><br>
<b>	unsigned int *pErrID );</b><br>
<br>
<b>	int ( *SetHeader )( FilterContext *pContext,</b><br>
<b>	char *pName,</b><br>
<b>	char *pValue,</b><br>
<b>	unsigned int *pErrID );</b><br>
<br>
<b>	int ( *AddHeader )( FilterContext *pContext,</b><br>
<b>	char *pHheader,</b><br>
<b>	unsigned int *pErrID );</b><br>
<br>
<b>	unsigned int reserved;</b><br>
<b>} FilterRawRequest;</b><br>
<br>
<b>requestMethod</b><b><i>: </i></b>is the request method. It can be one of the following:
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
pErrID is a pointer to an unsigned integer that is set to 0 if successful, to DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the result, and DSAPI_INVALID_ARGUMENT for invalid arguments passed.<br>
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
<b>reserved </b>is reserved for future use.<br>
</ul>
</ul>
<b>kFilterParsedRequest Event</b><br>
All filters currently loaded and supporting this event, are notified with this event when the http stack has finished pre-parsing all the http input headers. Note that this reflects the same state as in the event kFilterRawRequest since the http stack pre-parses the http input headers before it starts calling any filter. Any filter once again can choose to process the request completely at this step. pEventData is a pointer to the structure, FilterParsedRequest.  Note that only two callback functions are provided.  You can only access the http input headers in this step.  With the kFilterRawRequest, you have the opportunity to change them as well.<br>

<ul>
<ul><b>t</b><b>ypedef struct {</b><br>
<b>	unsigned int requestMethod;</b><br>
<br>
<b>	int ( *GetAllHeaders )( FilterContext *pContext,</b><br>
<b>	char **ppHeaders,</b>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul><b>unsigned int *pErrID );</b><br>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
<b>	int ( *GetHeader )( FilterContext *pContext,</b><br>
<b>	char *pName,</b><br>
<b>	char *pBuffer,</b><br>
<b>	unsigned int bufferSize,</b><br>
<b>	unsigned int *pErrID );</b><br>
<br>
<b>	unsigned int reserved;</b><br>
<b>} FilterParsedRequest;</b><br>
<br>
<b>requestMethod:</b><b><i> </i></b>is the request method. It can be one of the following:
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
Returns the byte count of the buffer containing the http input headers.<br>
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
pErrID is a pointer to an unsigned integer that is set to 0 if successful, to DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the result, and DSAPI_INVALID_ARGUMENT for invalid arguments passed.<br>
</ul>
</ul>
</ul>
<b>kFilterRewriteURL Event</b><br>
All filters currently loaded and supporting this event have the opportunity to change the URL to redirect the request to some other resource. If a filter successfully rewrites the URL to be processed, and the server processes the new URL, then the DSAPI layer stops processing this event, i.e., no other filters in the list are notified. pEventData is a pointer to an instance of the structure, FilterMapURL<i>. </i>Note that the structure, FilterMapURL is also used in the events, kFilterTranslateRequest and kFilterPostTranslate.<br>

<ul>
<ul><b>typedef struct {</b><br>
<b>	const char* url;</b><br>
<b>	char*	pathBuffer;</b><br>
<b>	unsigned int bufferSize;</b><br>
<b>	unsigned int mapType;</b><br>
<b>} FilterMapURL;</b><br>
<br>
<b>url:</b> Input parameter. It is a pointer to a string whose value is the current URL being processed.<br>
<br>
<b>pathBuffer:</b><b><i> </i></b>Output parameter. It is a pointer to a supplied buffer where the new URL is to be stored.<br>
<br>
<b>bufferSize:</b> Input parameter. This is the size of the supplied buffer in which to store the new URL.<br>
<br>
<b>mapType:</b> Output parameter. Not used in this case. <br>
</ul>
</ul>
<br>
<b>kFilterAuthenticate Event</b><br>
This event occurs when the http stack is in the authentication phase of the process. The filter code can view the request and user credentials, authenticate the user for the http stack, or completely handle the request. pEventData is a pointer to an instance of the structure.<br>

<ul>
<ul><b>typedef struct {</b><br>
<b>	LMBCS* userName;</b><br>
<b>	LMBCS* password;</b><br>
<b>	unsigned char* clientCert;</b><br>
<b>	unsigned int clientCertLen;</b><br>
<b>	unsigned int authFlags;</b><br>
<b>	unsigned int preAuthenticated;</b><br>
<b>	unsigned int foundInCache;</b><br>
<b>	unsigned int authNameSize;</b><br>
<b>	LMBCS* authName;</b><br>
<b>	unsigned int authType;</b><br>
<br>
<b>	int ( *GetUserNameList )( FilterContext *pContext, </b>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul><b>LMBCS *pBuffer,</b></ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
<b>	unsigned int bufferSize,</b><br>
<b>	unsigned int *pNumNames,</b><br>
<b>	unsigned int reserved,</b><br>
<b>	unsigned int *pErrID );</b><br>
<br>
<b>	int ( *GetHeader )( FilterContext *pContext,</b></ul>
</ul>
<b>	char *pName,</b>
<ul>
<ul><b>	char *pBuffer,</b><br>
<b>	unsigned int bufferSize,</b><br>
<b>	unsigned int *pErrID );</b></ul>
</ul>
<b>   </b><br>
<b>		void ( *GetMappedResource )( FilterContext *pContext,</b><br>
<b>char **ppBuffer,</b><br>
<b>unsigned int *pErrID );</b><br>

<ul>
<ul><b>} FilterAuthenticate;</b><br>
<br>
<b>userName:</b> Input parameter. The user's web name from the input request. It is set to NULL if none is available.<br>
<br>
<b>password:</b><b><i> </i></b>Input parameter. The user's web password from the input request. It is set to NULL if none is available.<br>
<br>
<b>clientCert :</b><b><i> </i></b>Input parameter. The SSL client certification. It is set to NULL if none is available.<br>
<br>
<b>clientCertLen:</b> Input parameter. The length of the SSL client certificate. It is set to zero in none is available.<br>
<br>
<b>authFlags:</b><b><i> </i></b>Input parameter. The authentication options that are enabled for the server. It can be one of more of the following &quot;OR&quot;ed together:<br>

<ul>
<ul>	kAuthAllowBasic: The server allows basic authentication by providing a user name and password.<br>
	kAuthAllowAnonymous: The server allows anonymous access to public (non protected) documents.<br>
	kAuthAllowSSLCert: The server allows SSL authentication using an SSL client certificate.<br>
	kAuthAllowSSLBasic:  <br>
	kAuthAllowSSLAnonymous: The server allows anonymous SSL authentication to public (non protected) documents.<br>
	kAuthRedirectToSSL: The server allows redirection to SSL authentication for documents that are SSL protected.<br>
</ul>
</ul>
<b>preAuthenticated:</b><b><i> </i></b>Input parameter. It is set to TRUE if the user has been already pre-authenticated presumably by a companion http stack (e.g., MS-IIS).<br>
<br>
<b>foundInCache:</b> Input parameter. It is set to TRUE if the user is already cached in Domino's internal cache and will be authenticated on that basis unless the filter handles the event. This member allows filters not to re-authenticate an already authenticated user. Filters in this case should immediately return <i>kFilterNotHandled</i>.<br>
<br>
<b>authNameSize:</b> Input parameter. This is the size of the buffer in which to store the authenticated user name. <br>
<br>
<b>authName:</b> Input parameter. It is a pointer to a supplied buffer where the authenticated user's name (canonical name) must be stored.<br>
<br>
<b>authType:</b> Output parameter. The filter, if it handles the event, must set this field to the type of authorization described by one of the following values:<br>

<ul>	kNotAuthentic: User's credentials failed authentication. The http stack must terminate the processing of the request. <br>
	kAuthenticBasic: User's name and password has passed authentication. The authentication phase should be terminated, and the next phase in the processing of the request started.<br>
	kAuthenticClientCert: The SSL authentication using an SSL client certificate has succeeded. The authentication phase should be terminated, and the next phase in the processing of the request started.<br>
</ul>
<b>int ( *GetUserNameList )( FilterContext *pContext, </b><br>
<b>	LMBCS *pBuffer,</b><br>
<b>	unsigned int bufferSize,</b>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>
<ul><b>unsigned int *pNumNames,</b></ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
<b>	unsigned int reserved,</b><br>
<b>	unsigned int *pErrID );</b>
<ul>This callback function allows a filter to gain access to the user's group list.<br>
<br>
Returns the number of bytes valid in the return buffer, -1 if the buffer is too small (the buffer is still filled to end). <br>
<br>
pContext is a pointer to the structure, FilterContext and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
pBuffer is a pointer to a memory buffer where to return the user's group list after it has been computed. The format is a sequence of zero terminated strings, i.e, &quot;&lt;group1\0group2\0...groupn\0&quot;.<br>
<br>
bufferSize is the size of the memory block pointed to by pBuffer.<br>
<br>
pNumNames is a pointer where to store the number of names contained in the user's group name list.<br>
<br>
reserved is reserved for future use. It should be set to 0.<br>
<br>
pErrID<i> </i>is a pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successful, to a non-zero value otherwise. The only valid non-zero status in this case is DSAPI_INVALID_ARGUMENT which indicates that one or more of the supplied arguments is(are) not valid.</ul>
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
pName<i> </i>is a pointer to a string containing the name of the desired http header. This cannot be NULL or an empty string.<br>
<br>
pBuffer is a pointer to a buffer where to store the result. This argument cannot be NULL.<br>
<br>
bufferSize is the size of supplied buffer.<br>
<br>
pErrID is a pointer to an unsigned integer that is set to 0 if successful, to DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the result, and DSAPI_INVALID_ARGUMENT for invalid arguments passed.<br>
</ul>
<b>void ( *GetMappedResource )( FilterContext *pContext, </b><br>
<b>					char **ppBuffer, </b><br>
<b>					unsigned int *pErrID );</b>
<ul>The GetMappedResource callback function retreives a mapped resource value. <br>
<br>
Returns 0 for for a hard failure (bad argument passed), the number of bytes valid in the buffer containing the result if successful, or the required buffer size if the buffer is too small to contain the result.<br>
<br>
pContext	- pointer to the structure FilterContext and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
ppBuffer	- pointer to a pointer to a buffer where to store the result. This argument cannot be NULL.<br>
pErrID	- pointer to an unsigned integer that is set to 0 if successful, to DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the result.<br>
</ul>
</ul>
</ul>
<br>
<b>kFilterUserNameList Event</b><br>
This event occurs when the http stack is about to generate the user's group name list. These are group names the user is a member of.  This event follows the kFilterAuthenticate event. The filter can have the Domino server populate the list, add or remove groups to/from the list or completely handle the event (generate completely the group list itself). The parameter in the function, HttpEventProc, pEventData, is a pointer to the structure, FilterUserNameList.<br>

<ul>
<ul><b>typedef struct {</b><br>
<b>	const LMBCS* userName;</b><br>
<br>
<b>	int ( *GetUserNameList )( FilterContext *pContext, </b><br>
<b>	LMBCS *pBuffer,</b><br>
<b>	unsigned int bufferSize,</b><br>
<b>	unsigned int *pNumNames,</b><br>
<b>	unsigned int reserved,</b><br>
<b>	unsigned int *pErrID );</b><br>
<br>
<b>	int ( *PopulateUserNameList )( FilterContext *pContext, </b><br>
<b>	LMBCS *pBuffer,</b><br>
<b>	unsigned int bufferSize,</b><br>
<b>	unsigned int *pNumNames,</b><br>
<b>	unsigned int reserved,</b><br>
<b>	unsigned int *pErrID );</b><br>
<br>
<b>	int ( *AddGroupsToList )( FilterContext *pCcontext, </b><br>
<b>	LMBCS *pGroupNames,</b><br>
<b>	unsigned int numGroupNames,</b><br>
<b>	unsigned int reserved,</b><br>
<b>	unsigned int *pErrID );</b><br>
<br>
<b>	int ( *RemoveGroupsFromList )( FilterContext *pContext, </b><br>
<b>	unsigned int reserved,</b><br>
<b>	unsigned int *pErrID );</b><br>
<br>
<b>	unsigned int reserved;</b><br>
<b>} FilterUserNameList;</b><br>
<br>
<b>userName:</b> the authenticated user name.<br>
<br>
<b>int ( *GetUserNameList )( FilterContext *pContext, </b><br>
<b>	LMBCS *pBuffer,</b><br>
<b>	unsigned int bufferSize,</b><br>
<b>	unsigned int *pNumNames,</b><br>
<b>	unsigned int reserved,</b><br>
<b>	unsigned int *pErrID );</b>
<ul>This callback function allows a filter to gain access to the user's group list.<br>
<br>
Returns the number of bytes valid in the supplied buffer, (-1) if the buffer is too small (although the buffer is filled to end).<br>
<br>
pContext is a pointer to the structure, FilterContext, and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
pBuffer is a pointer to a memory buffer where to return the user's group list after it has been computed. The format is sequence of zero terminated strings, i.e., &quot;&lt;group1\0group2\n...groupn\0&gt;&quot;.<br>
<br>
bufferSize is the size of the memory block pointed to by pBuffer.<br>
<br>
pNumNames is a pointer where to store the number of names contained in the user's group list.<br>
<br>
reserved is reserved for future use. It should be set to 0.<br>
<br>
pErrID is a pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successful, to a non-zero value otherwise. The only valid non-zero status in this case is DSAPI_INVALID_ARGUMENT which indicates that one or more of the supplied arguments is(are) not valid.</ul>
<br>
<b>int ( *PopulateUserNameList )( FilterContext *pContext, </b><br>
<b>	LMBCS *pBuffer,</b><br>
<b>	unsigned int bufferSize,</b><br>
<b>	unsigned int *pNumNames,</b><br>
<b>	unsigned int reserved,</b><br>
<b>	unsigned int *pErrID );</b>
<ul>This callback function allows a filter to request that the user's group list be computed and returned in the supplied buffer.<br>
<br>
Returns the number of valid bytes returned in <i>pBuffer.</i><br>
<br>
pContext is a pointer to the structure, FilterContext, and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
pBuffer is a pointer to a memory buffer where to return the user's group list after it has been computed.<br>
<br>
bufferSize is the size of the memory block pointed to by pBuffer.<br>
<br>
pNumNames is a pointer where to store the number of names contained in the user's group list.<br>
<br>
reserved is reserved for future use. It should be set to 0.<br>
<br>
pErrID is a pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successful, to a non-zero value otherwise.</ul>
<br>
<b>int ( *AddGroupsToList )( FilterContext *pCcontext, </b><br>
<b>	LMBCS *pGroupNames,</b><br>
<b>	unsigned int numGroupNames,</b><br>
<b>	unsigned int reserved,</b><br>
<b>	unsigned int *pErrID );</b>
<ul>This callback function allows the filter to dynamically augment the user's group.<br>
<br>
Returns TRUE if successful, FALSE otherwise<br>
<br>
pContext is a pointer to the structure, FilterContext, and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
pBuffer is a pointer to a buffer that contains the names to add to the user's group list. The format is a list of strings each of which contains the group name, i.e., <i>&lt; string1 string2 ... stringn &gt;. </i>Strings here are defined as C strings, i.e., a NULL terminated sequence of bytes.<br>
<br>
numGroupName is the number of group names contained in the <i>pBuffer.</i><br>
<br>
reserved is reserved for future use. It should be set to 0.<br>
<br>
pErrID<i> </i>a pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successful, to a non-zero value otherwise. In this case it is always set to 0.</ul>
<br>
<b>int ( *RemoveGroupsFromList )( FilterContext *pContext, </b><br>
<b>	unsigned int reserved,</b><br>
<b>	unsigned int *pErrID );</b>
<ul>This callback allows the filter to clear the user's group list. The result is a group list that contains only the user's known names.<br>
<br>
Return TRUE<br>
<br>
pContext is a pointer to the structure, FilterContext, and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
reserved is reserved and should be always set to 0.<br>
<br>
pErrID is a pointer to an unsigned integer where to store a status code. The status code is always set to 0.</ul>
<br>
<b>reserved:</b> is reserved for future use.<br>
</ul>
</ul>
Note that the altered group names list is not seen by the current implementation of Domino's agents (agents compute their own group names list based on the authenticated user name).<br>
<br>
<br>
<b>kFilterTranslateRequest Event</b><br>
This event occurs when the http stack is about to translate the path URL to a target resource. The filter can translate the request using its own translation and mapping rules, or completely handle the request. pEventData points to an instance of the structure, FilterMapURL<i>. </i>The structure, FilterMapURL, is described below:<br>

<ul>
<ul><b>typedef struct {</b><br>
<b>	const char* url;</b><br>
<b>	char*	pathBuffer;</b><br>
<b>	unsigned int bufferSize;</b><br>
<b>	unsigned int mapType;</b><br>
<b>} FilterMapURL;</b><br>
<br>
<b>url:</b> Input parameter. It is a pointer to a string whose value is the current URL being processed.<br>
<br>
<b>pathBuffer: </b>Output parameter. It is a pointer to a supplied buffer where the resulting target resource path is to be stored.<br>
<br>
<b>bufferSize:</b> Input parameter. This is the size of the supplied buffer in which to store the target resource path .<br>
<br>
<b>mapType:</b> Output parameter. It is one of the following:</ul>
</ul>
	typedef enum {<br>
		kURLMapUnknown	= 0,<br>
		kURLMapPass = 1,	<br>
		kURLMapExec = 2,<br>
		kURLMapRedirect = 3,<br>
		kURLMapService = 4,<br>
		kURLMapDomino = 5<br>
		} FilterURLMapTypes;<br>
<br>
		where
<ul>
<ul>
<ul>
<ul>	kURLMapUnknown: Unknown mapping type.<br>
	kURLMapPass: File system mapping rule<br>
	kURLMapExec: CGI mapping rule<br>
	kURLMapRedirect: Redirect mapping rule<br>
	kURLMapService: Obsolete.  No longer used.<br>
	kURLMapDomino: Domino mapping rule<br>
</ul>
</ul>
</ul>
</ul>
Note:  The kFilterMapURL event is the same as the KFilterTranslateRequest event.<br>
<br>
<br>
<b>kFilterPostTranslate Event</b><br>
This event occurs after the event, kFilterTranslateEvent, has been handled.  It is an opportunity for the filter to change the target resource to be accessed. The filter can change both the target resource path and the mapping type. The filter can also choose to completely service the request. pEventData is a pointer to the structure, FilterMapURL. The structure, FilterMapURL, is described below:<br>

<ul>
<ul><b>typedef struct {</b><br>
<b>	const char* url;</b><br>
<b>	char*	pathBuffer;</b><br>
<b>	unsigned int bufferSize;</b><br>
<b>	unsigned int mapType;</b><br>
<b>} FilterMapURL;</b><br>
<br>
<b>url:</b> Input parameter. It is a pointer to a string whose value is the current URL being processed.<br>
<br>
<b>pathBuffer: </b>Input<b>/</b>Output parameter. It is a pointer to a supplied buffer containing the already computed path to the target resource. The new target resource path is to be stored in this buffer.<br>
<br>
<b>bufferSize:</b> Input parameter. This is the size of the supplied buffer in which to store the target resource path .<br>
<br>
<b>mapType:</b> Input/Output parameter. It is one of the following:</ul>
</ul>
	typedef enum {<br>
		kURLMapUnknown	= 0,<br>
		kURLMapPass = 1,	<br>
		kURLMapExec = 2,<br>
		kURLMapRedirect = 3,<br>
		kURLMapService = 4,<br>
		kURLMapDomino = 5<br>
		} FilterURLMapTypes;<br>
<br>
		where
<ul>
<ul>
<ul>
<ul>	kURLMapUnknown: Unknown mapping type.<br>
	kURLMapPass: File system mapping rule<br>
	kURLMapExec: CGI mapping rule<br>
	kURLMapRedirect: Redirect mapping rule<br>
	kURLMapService: Obsolete.  No longer used.<br>
	kURLMapDomino: Domino mapping rule<br>
<br>
</ul>
</ul>
</ul>
</ul>
<b>kFilterAuthorized Event</b><br>
This event occurs after the authentication phase has taken place and the user's group names list has been computed. The filter can override the default implementation of the authorization phase and grant or deny access to the target resource. pEventData is a pointer to the structure, FilterAuthorize.  It contains information about the target resource to serve.  Note that the filter can get access to the authenticated user information by using the services via the ServerSupport callback with the flag, kGetAuthenticatedUserInfo. This will allow the user to gain access to the user's authenticated name as well as to his/her group names list. <br>
<br>
If the filter denies access to the target resource, it must send the appropriate response to the client, and set the field, isAuthorized, in the FilterAuthorize structure to 0. It can then return either kFilterHandledRequest or kFilterHandledEvent.  The DSAPI layer will then signal the http stack to terminate the processing of the current request.<br>
<br>
The structure FilterAuthorize is described below:<br>

<ul>
<ul><b>typedef struct _FilterAuthorize{</b><br>
<b>	const char		*pURL;</b><br>
<b>	char			*pBuffer;</b><br>
<b>	unsigned int	bufferSize;</b><br>
<b>	unsigned int	mapType;</b><br>
<b>	unsigned int	isAuthorized;</b><br>
<b>} FilterAuthorize</b>;<br>
<br>
<br>
<b>pURL:</b> Input parameter. It is the http request URL.<br>
<br>
<b>pBuffer:</b><b><i> </i></b>Input parameter. This buffer contains the path to the target resource.<br>
<br>
<b>bufferSize:</b><b><i> </i></b>Input parameter. This is the total size in bytes of the supplied buffer.<br>
<br>
<b>mapType:</b> Input parameter. It is one of the following:
<ul>
<ul>	typedef enum {</ul>
</ul>
</ul>
</ul>
		kURLMapUnknown	= 0,<br>
		kURLMapPass = 1,	<br>
		kURLMapExec = 2,<br>
		kURLMapRedirect = 3,<br>
		kURLMapService = 4,<br>
		kURLMapDomino = 5<br>
		} FilterURLMapTypes;<br>
<br>
		where
<ul>
<ul>
<ul>
<ul>	kURLMapUnknown: Unknown mapping type.<br>
	kURLMapPass: File system mapping rule<br>
	kURLMapExec: CGI mapping rule<br>
	kURLMapRedirect: Redirect mapping rule<br>
	kURLMapService: Obsolete.  No longer used.<br>
	kURLMapDomino: Domino mapping rule<br>
</ul>
</ul>
<b>isAuthorized: </b>Output parameter. It is set to 1 if the user is granted access to the resource, 0 otherwise.</ul>
</ul>
<br>
<br>
<b>kFilterProcessRequest Event</b><br>
This is the last step in servicing an http request. This event can be used to override the default implementation of the processing of the request.  In this phase the response data is computed and sent to the client.  pEventData is a pointer to the structure, FilterMapURL.<i> </i>The structure, FilterMapURL, is described below:
<ul>
<ul><b>typedef struct {</b><br>
<b>	const char* url;</b><br>
<b>	char*	pathBuffer;</b><br>
<b>	unsigned int bufferSize;</b><br>
<b>	unsigned int mapType;</b><br>
<b>} FilterMapURL;</b><br>
<br>
<b>url:</b> Input parameter. It is a pointer to a string whose value is the current URL being processed.<br>
<br>
<b>pathBuffer: </b>Input parameter. It is a pointer to a supplied buffer containing the already computed path to the target resource.<br>
<br>
<b>bufferSize:</b> Input parameter. This is the size of the supplied buffer in which to store the target resource path.<br>
<br>
<b>mapType:</b> Input parameter. It is one of the following:<br>
</ul>
</ul>
	typedef enum {<br>
		kURLMapUnknown	= 0,<br>
		kURLMapPass = 1,	<br>
		kURLMapExec = 2,<br>
		kURLMapRedirect = 3,<br>
		kURLMapService = 4,<br>
		kURLMapDomino = 5<br>
		} FilterURLMapTypes;<br>
<br>
		where
<ul>
<ul>
<ul>
<ul>	kURLMapUnknown: Unknown mapping type.<br>
	kURLMapPass: File system mapping rule<br>
	kURLMapExec: CGI mapping rule<br>
	kURLMapRedirect: Redirect mapping rule<br>
	kURLMapService: Obsolete.  No longer used.<br>
	kURLMapDomino: Domino mapping rule<br>
<br>
</ul>
</ul>
</ul>
</ul>
<b>kFilterEndRequest Event</b><br>
This event is used to advise the filter code that it is time to clean up and release resources allocated to handle a given http request.  pEventData is NULL in this case.<br>
<br>
<b>kFilterAuthUser Event</b><br>
This event is replaced with the kFilterAuthenticate event, but is still supported for compatibility with previously written DSAPI filters.  In this event, the filter authenticates the web user.  pEventData is an instance of the structure, FilterAuthenticate.<i> </i>The structure is described fully in the kFilterAuthenticate event described above.<br>
<br>
This event allows you to customize the authentication of the Web users, which is often one part of implementing 'single-sign on' within a corporation.  In this case, the DSAPI filter is notified when Domino authenticates a user.  The DSAPI filter can then parse the user name, validate user names and passwords against a legacy mainframe system, and if successful, notify the Domino Web server that it has handled the user's authentication and return to Domino the user's credentials.<br>
<br>
This is a guide to setting the output variables and return code for common authentication scenarios where eventData points to the FilterAuthenticate structure:<br>

<ul type="disc">
<li><u>Scenario 1</u>: The filter was able to authenticate the user.<br>
Set eventData-&gt;authName to the canonical name, set eventData-&gt;authType to kAuthenticBasic or kAuthenticClientCert, and the return code to kFilterHandledEvent.</ul>

<ul type="disc">
<li><u>Scenario 2</u>: The filter was NOT able to authenticate the user, and other filters or Domino should go ahead and attempt their own authentication.<br>
Set the return code to kFilterNotHandled.</ul>

<ul type="disc">
<li><u>Scenario 3</u>: The filter was NOT able to authenticate the user, and other filters or Domino should NOT attempt their own authentication.<br>
Set eventData-&gt;authType to kNotAuthentic, and the return code to kFilterHandledEvent.<br>
</ul>
<b>kFilterResponse Event</b><br>
This event occurs when the http stack is about to send the http response headers to the client. This gives a chance to the filter to change the response that is sent to the client. This is not completely implemented in the current version of DSAPI. <i>pEventData</i> is a pointer to an instance of the structure <i>FilterResponse</i> and is described below:<br>
<br>
<b><i>typedef struct {</i></b><br>
<b><i>	unsigned int	responseCode;</i></b><br>
<b><i>	char*			reasonText;</i></b><br>
<br>
<b><i>	int ( *GetAllHeaders )( FilterContext *pContext,</i></b><br>
<b><i>	char **ppHeaders,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
<br>
<b><i>	int ( *GetHeader )( FilterContext *pContext,</i></b><br>
<b><i>	char *pName,</i></b><br>
<b><i>	char *pBuffer,</i></b><br>
<b><i>	unsigned int bufferSize,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
<br>
<b><i>	int ( *SetHeader )( FilterContext *pContext,</i></b><br>
<b><i>	char *pName,</i></b><br>
<b><i>	char *pValue,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
<br>
<b><i>	int ( *AddHeader )( FilterContext *pContext,</i></b><br>
<b><i>	char *pHeader,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
<br>
<b><i>	unsigned int	reserved;</i></b><br>
<b><i>	char*			userName;</i></b><br>
<b><i>} FilterResponse;</i></b><br>
<br>
responseCode<b> -</b> Input parameter. It is the HTTP Response status code.<br>
<br>
reasonText<b> - </b>Input parameter. It is the HTTP response status text if any.<br>
<br>
<b><i>int ( *GetAllHeaders )( FilterContext *pContext,</i></b><br>
<b><i>	char** ppHeaders,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
This callback function allows the filter to gain access to the response http headers.<br>
<br>
Returns the byte count of the buffer containing the http response headers.<br>
<br>
pContext - is a pointer to the structure <i>FilterContext</i> and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
ppHeaders - is a pointer to a location where the DSAPI layer will store the pointer to a buffer that will contain the response http headers.<br>
<br>
pErrID - is a pointer to an unsigned integer that is set to 0 if successfull, to an error code otherwise. Possible error codes are: DSAPI_INVALID_ARGUMENT, DSAPI_MEMORY_ERROR and DSAPI_INTERNAL_ERROR.<br>
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
pContext - is a pointer to the structure <i>FilterContext</i> and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
pName - is a pointer to a string containing the name of the desired http header. This cannot be equal to NULL nor to an empty string.<br>
<br>
pBuffer - is a pointer to a buffer where to store the result. This argument cannot be NULL.<br>
<br>
bufferSize - is the size of supplied buffer.<br>
<br>
pErrID - is a pointer to an unsigned integer that is set to 0 if successfull, to DSAPI_BUFFER_TOO_SMALL if the supplied buffer is too small to contain the result.<br>
<br>
<b><i>int ( *SetHeader )( FilterContext *pContext,</i></b><br>
<b><i>	char *pName,</i></b><br>
<b><i>	char *pValue,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
This callback function allows a filter to change the value of an existing response http header. Note that if the http header does not exist, it is added to the list of http response headers.<br>
<br>
Returns TRUE if successfull, FALSE otherwise.<br>
<br>
pContext - is a pointer to the structure <i>FilterContext</i> and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
pName - is a pointer to a string containing the name of the http header to change. This argument cannot be NULL or an empty string.<br>
<br>
pValue - is a pointer to a string containing the value for the http header.<br>
<br>
pErrID - is a pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successfull, to a non zero value otherwise.<br>
<br>
<b><i>int ( *AddHeader )( FilterContext *pContext,</i></b><br>
<b><i>	char *pHheader,</i></b><br>
<b><i>	unsigned int *pErrID );</i></b><br>
This callback function allows a filter to add an http header to the list of the response http headers. Note that if the http header already exists, its value is changed to reflect the new value.<br>
<br>
Return TRUE if successfull, FALSE otherwise.<br>
<br>
pContext - is a pointer to the structure <i>FilterContext</i> and contains all the context data needed by the DSAPI layer implementation to identify which request this pertains to.<br>
<br>
pHeader - is a pointer to a valid http header. The expected format is the same as the format of response http headers, i.e., <i>&lt;headerName:value&gt;.</i><br>
<br>
pErrID - is a pointer to an unsigned integer where to store a status code. The status code is set to 0 if the operation is successfull, to a non zero value otherwise. The only non zero in this case is DSAPI_INVALID_ARGUMENT which indicates that an error in the format of the supplied header has been detected.<br>
<br>
reserved - is reserved for future use.<br>
<br>
<b>kFilterRawWrite Event</b><br>
This event occurs when the http stack is about to send the http response data to the client. This gives a chance to the filter to change the response data that is sent to the client. This is not completly implemented in the current version of DSAPI. <i>pEventData </i>is a pointer to an instance of the structure <i>FilterRawWrite</i> and is described below:<br>
<br>

<ul>
<ul><b><i>typedef struct {</i></b><br>
<b><i>	char*	content;</i></b><br>
<b><i>	unsigned int	contentLen;</i></b><br>
<b><i>	unsigned int	reserved;</i></b><br>
<b><i>} FilterRawWrite;</i></b><br>
</ul>
</ul>
content -<b> </b>Input/Output parameter. It is a pointer to a buffer that contains the data to send to the client. The filter can change the data in place (using the same buffer) or allocate a new buffer and fill it.<br>
<br>
contentLen<b> - </b>Input/Output parameter. It is the number of valid bytes in the supplied buffer on input, and/or the number of valid bytes in the buffer on output.<br>
<br>
reserved<b> -</b> reserved for future use.<br>
<br>
<br>
<b><font size="5" color="#000080">Running and Programming Considerations</font></b><br>
 
<ul type="disc">
<li>A DSAPI filter is built as a shared library under UNIX and a DLL under Win32.   DSAPI is supported on all Domino server platforms.  The details of compiling and linking a shared library differ from platform to platform.  Please refer to <b><font color="#000080">Chapter 3, Platform Specifics, </font></b>for further information on building applications for a particular platform.  </ul>

<ul type="disc">
<li>Since the filter is written in C, you can use the Notes C API to access Domino data or other C interfaces to access other systems.</ul>

<ul type="disc">
<li>A DSAPI filter is a server extension, the filter has the privileges of the server ID when accessing Domino databases through the C API.</ul>

<ul type="disc">
<li>Since filter notification functions may be called simultaneously from different server threads, all filter code must be thread-safe. When a Domino server thread receives an HTTP request, it allocates a new instance of the FilterContext structure. As the thread processes the request, it passes that instance to all filter functions it calls. FilterContext contains a pointer, privateContext, that you can use to store your own data structure. All thread-specific data that the filter needs to maintain from event to event should be stored in your privateContext structure.</ul>

<ul type="disc">
<li>You should use the AllocMem callback function to allocate dynamic memory in your filter. All memory allocated by AllocMem is automatically freed when the server thread finishes processing the request. This simplifies your filter cleanup and ensures that the memory is freed even if the thread terminates abnormally.</ul>

<ul type="disc">
<li>Install the filter by specifying the name of the filter in the Server record, in the field DSAPI filter file name in the Internet Protocols -&gt; HTTP table. You can specify just the name of the filter file if it is located in the Domino program or data directories; otherwise you must specify the fully-qualified path name.  Make sure that all filter files are secured by adequate file permissions and physical security, to prevent unauthorized persons from tampering with the filter.</ul>
<br>
<b><font size="5" color="#000080">DSAPI Sample Code</font></b><br>
<br>
The purpose of this example is to show how to extend the Domino Web server to enable Unix password checking.  When a Domino database is accessed via a Web browser, Domino can authenticate the user based on Unix password (i.e., password stored in standard Unix password registries such as /etc/passwd or NIS).  It is possible to cut and paste what is documented here and incorporate it into a sample of your own.  Steps for running and installing the filter are featured below.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b><font color="#000080">What the sample code illustrates.</font></b></td></tr>
</table>
When a protected Web page is accessed, Domino will prompt for a user name and password.  This example allows the user to enter a Unix password, and to be authenticated for Web access if the password can be verified. This example works only for the case where a user is known to both Domino and Unix.  <br>
The example assumes that the Unix user name is the user's Domino &quot;short  name&quot;.  For instance: <br>
		<u>Domino user name</u>    	Jane Doe <br>
		<u>Domino short name</u>   	jdoe <br>
		<u>Unix user name</u>      	jdoe (note:  Unix is case sensitive, so the Domino short name should be stored as lower case characters.  For best  					interoperability, this name should be no longer than 8 characters.) 
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b><font color="#000080">Installing and running the filter shared library.</font></b></td></tr>
</table>
<b>1.	</b><u>Filter Installation</u><br>

<ul type="disc">
<li>Open the Domino Name and Address book.  Switch to the server view and open the server document.  Edit the server document:
<li>Click on the &quot;Internet Protocols&quot; tab.
<li>Click on the &quot;HTTP&quot; tab.
<li>Edit the field &quot;DSAPI filter file name&quot; to contain the name of the shared library. (If the shared library is installed to a  directory other than the Domino                           executable directory, provide a full path name to the library).
<li>Save your changes.</ul>
<br>
<b>2.	</b><u>Running the filter</u><br>

<ul type="disc">
<li>Gain access to the server console. Restart the Domino server http task (e.g., issue commands &quot;tell http quit&quot;, &quot;load http&quot;).  The server console should display an initialization message as the shared library is loaded.
<li>From a Domino admin client, register a new Domino user, ensuring that the user's Domino short name corresponds to the desired Unix login username.  Or find an existing Domino user who is already known to both Domino and Unix.
<li>For the target Domino database that will be accessed from a Web browser, edit the database access control list to grant access to the Domino user.
<li>Use a Web browser to access the target database.  If the example is working properly, you should be prompted for user name and password.  Enter the Unix password to test the example.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b><font color="#000080">Program Filter Initialization, Filter Termination and Filter Notification Definitions.</font></b></td></tr>
</table>
</ul>
<tt><font size="2">/* Input and output include files */</font></tt><br>
<tt><font size="2">#include &lt;stdlib.h&gt;</font></tt><br>
<tt><font size="2">#include &lt;stdio.h&gt;</font></tt><br>
<tt><font size="2">#include &lt;string.h&gt;</font></tt><br>
<br>
<tt><font size="2">/* Special dsapi include file */</font></tt><br>
<tt><font size="2">#include &quot;dsapi.h&quot;</font></tt><br>
<br>
<tt><font size="2">/* unix authentication includes */</font></tt><br>
<br>
<tt><font size="2">#ifdef AIX</font></tt><br>
<tt><font size="2">#include &lt;sys/types.h&gt;</font></tt><br>
<tt><font size="2">#include &lt;pwd.h&gt;</font></tt><br>
<tt><font size="2">#endif</font></tt><br>
<br>
<tt><font size="2">/* Notes SDK include files */</font></tt><br>
<tt><font size="2">#include &quot;global.h&quot;</font></tt><br>
<tt><font size="2">#include &quot;osmem.h&quot;</font></tt><br>
<tt><font size="2">#include &quot;lookup.h&quot;</font></tt><br>
<br>
<tt><font size="2">/*---</font></tt><br>
<tt><font size="2">*		local procedure prototypes</font></tt><br>
<tt><font size="2">*/</font></tt><br>
<br>
<tt><font size="2">/* Notes SDK unix shared library entrypoint */</font></tt><br>
<tt><font size="2">STATUS FAR PASCAL MainEntryPoint (void);</font></tt><br>
<br>
<tt><font size="2">/* Routines with syntax dictated by the DSAPI interface */</font></tt><br>
<tt><font size="2">unsigned int Authenticate(FilterContext* context, FilterAuthenticate* authData);</font></tt><br>
<br>
<tt><font size="2">/* Retrieval of names from Notes name and address book */</font></tt><br>
<tt><font size="2">int getUserNames (FilterContext* context, char *userName, char **pUserFullName, int &nbsp;*pUserFullNameLen,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char **pUserShortName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; int &nbsp;*pUserShortNameLen);</font></tt><br>
<br>
<tt><font size="2">int getLookupInfo (FilterContext* context, char *pMatch, int &nbsp;itemNumber, char **pInfo, int &nbsp;*pInfoLen);</font></tt><br>
<br>
<tt><font size="2">/* unix password check routine */</font></tt><br>
<tt><font size="2">int unixAuthenticate(char *userName, char *password);</font></tt><br>
<br>
<tt><font size="2">/*---</font></tt><br>
<tt><font size="2">*		local procedures follow</font></tt><br>
<tt><font size="2">*/</font></tt><br>
<br>
<tt><font size="2">STATUS FAR PASCAL MainEntryPoint (void) </font></tt><br>
<tt><font size="2">{</font></tt><br>
<tt><font size="2">/*</font></tt><br>
<tt><font size="2">&nbsp;* Description: &nbsp;Provide a main entry point for the Notes API to </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; initialize inside of this shared library. &nbsp;We need </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; this entry point because we want to be able to lookup</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; user information in the name and address book via the</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Notes SDK API.</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Input: &nbsp;nothing</font></tt><br>
<tt><font size="2">&nbsp;* Output: nothing</font></tt><br>
<tt><font size="2">&nbsp;* Return: NOERROR</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<tt><font size="2">	return NOERROR;</font></tt><br>
<tt><font size="2">}</font></tt><br>
<br>
<tt><font size="2">/*---</font></tt><br>
<tt><font size="2">*		filter initialization</font></tt><br>
<tt><font size="2">*/</font></tt><br>
<tt><font size="2">unsigned int FilterInit(FilterInitData* filterInitData)</font></tt><br>
<tt><font size="2">{</font></tt><br>
<tt><font size="2">/*</font></tt><br>
<tt><font size="2">&nbsp;* Description: &nbsp;Filter initialization is performed when the filter</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; shared library is dynamically loaded.</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Input: &nbsp;filterInitData &nbsp; &nbsp; dsapi specification controls the format</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;of data</font></tt><br>
<tt><font size="2">&nbsp;* Output: filterInitData &nbsp; &nbsp; several fields are filled in</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Return: kFilterHandledEvent</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /*Required*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; filterInitData-&gt;appFilterVersion = kInterfaceVersion; &nbsp;</font></tt><br>
<br>
<tt><font size="2">	/* Modify the following code to set the flags you want */</font></tt><br>
<tt><font size="2">	filterInitData-&gt;eventFlags = </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; kFilterAuthUser;</font></tt><br>
<tt><font size="2">	</font></tt><br>
<tt><font size="2">	/* Set a short description for your filter */</font></tt><br>
<tt><font size="2">	strcpy(filterInitData-&gt;filterDesc,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;Unix Authentication Filter&quot;);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /* insert any global initialization code here... &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">	/* Output sent to stdout and stderr is displayed on the </font></tt><br>
<tt><font size="2">	 * server console, but is not written to the server log file.</font></tt><br>
<tt><font size="2">	 */</font></tt><br>
<tt><font size="2">	printf(&quot;\nDSAPI Unix Authentication filter initialized\n&quot;);</font></tt><br>
<tt><font size="2">	return kFilterHandledEvent;</font></tt><br>
<tt><font size="2">}</font></tt><br>
<br>
<tt><font size="2">/*---</font></tt><br>
<tt><font size="2">*		filter termination</font></tt><br>
<tt><font size="2">*/</font></tt><br>
<tt><font size="2">unsigned int TerminateFilter(unsigned int reserved)</font></tt><br>
<tt><font size="2">{</font></tt><br>
<tt><font size="2">/*</font></tt><br>
<tt><font size="2">&nbsp;* Description: &nbsp;Filter termination is performed when the filter</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; shared library is unloaded.</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Input: &nbsp;reserved &nbsp; &nbsp; currently unused (dsapi spec controls the</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;format of data)</font></tt><br>
<tt><font size="2">&nbsp;* Output: none</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Return: kFilterHandledEvent</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<tt><font size="2">	/* insert any global cleanup code here... */</font></tt><br>
<br>
<tt><font size="2">	printf(&quot;\nDSAPI Unix authentication filter unloaded\n&quot;);</font></tt><br>
<tt><font size="2">	return kFilterHandledEvent;</font></tt><br>
<tt><font size="2">}</font></tt><br>
<br>
<br>
<tt><font size="2">/*---</font></tt><br>
<tt><font size="2">*		filter notification handling</font></tt><br>
<tt><font size="2">*/</font></tt><br>
<tt><font size="2">unsigned int HttpFilterProc(FilterContext* context,</font></tt><br>
<tt><font size="2">			unsigned int eventType, void* eventData)</font></tt><br>
<tt><font size="2">{</font></tt><br>
<tt><font size="2">/*</font></tt><br>
<tt><font size="2">&nbsp;* Description: &nbsp;This routine is called for all dsapi filter events. &nbsp;</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Input: &nbsp;reserved &nbsp; &nbsp; currently unused (dsapi spec controls the</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;format of data)</font></tt><br>
<tt><font size="2">&nbsp;* Output: none</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Return: kFilterNotHandled for all events that we don't customize, </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; otherwise allow our filter routine to provide a return</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; value.</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<tt><font size="2">	</font></tt><br>
<tt><font size="2">	/* Include only those events we want to handle */</font></tt><br>
<tt><font size="2">	switch (eventType) {</font></tt><br>
<tt><font size="2">	case kFilterAuthUser:</font></tt><br>
<tt><font size="2">		return Authenticate(context,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (FilterAuthenticate *)eventData);</font></tt><br>
<tt><font size="2">	default:</font></tt><br>
<tt><font size="2">		break;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<br>
<tt><font size="2">	return kFilterNotHandled;</font></tt><br>
<tt><font size="2">}</font></tt><br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b><font color="#000080">Filter Authentication Main Functionality which controls the authentication from both the Domino and Unix side.</font></b></td></tr>
</table>
<tt><font size="2">/*---</font></tt><br>
<tt><font size="2">*		handle user authentication</font></tt><br>
<tt><font size="2">*/</font></tt><br>
<tt><font size="2">unsigned int Authenticate(FilterContext* context,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; FilterAuthenticate* authData)</font></tt><br>
<tt><font size="2">{</font></tt><br>
<tt><font size="2">/*</font></tt><br>
<tt><font size="2">&nbsp;* Description: &nbsp;This routine is called on a dsapi kFilterAuthUser</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; event.</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Input: &nbsp;context &nbsp; &nbsp; dsapi specification controls the format of data</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; authData &nbsp; &nbsp;password field contains the password to use for </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; authentication userName field contains the name </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; to authenticate foundInCache field is TRUE if </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; user has been found in the cache and can be</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; authenticated on that basis.</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Output: authData &nbsp; &nbsp;authName field is filled with user's </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; distinguished name authType filed is filled </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; with kNotAuthentic if we can't authenticate the</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; unix user kAuthenticBasic if we can </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; authenticate the unix user.</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Return: kFilterNotHandled if we do not understand the input data, </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; or if the user has been found in the cache, or </font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if we find that the user to be authenticated is</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; not known to unix.</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; kFilterHandledEvent if the user is known to unix.</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<tt><font size="2">	/* If the user is found in the cache, then we don't need to do</font></tt><br>
<tt><font size="2">	 * anything further.</font></tt><br>
<tt><font size="2">	 */</font></tt><br>
<tt><font size="2">	if (!authData || authData-&gt;foundInCache)</font></tt><br>
<tt><font size="2">		return kFilterNotHandled;</font></tt><br>
<br>
<tt><font size="2">	/* Attempt to verify the user's password. </font></tt><br>
<tt><font size="2">	 */</font></tt><br>
<tt><font size="2">	if (authData-&gt;userName &amp;&amp; authData-&gt;password) {</font></tt><br>
<tt><font size="2">		char *fullName = NULL;</font></tt><br>
<tt><font size="2">		int fullNameLen = 0;</font></tt><br>
<tt><font size="2">		char *shortName = NULL;</font></tt><br>
<tt><font size="2">		int shortNameLen = 0;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Lookup the user in the Name and Address book. &nbsp;Get </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* the user's short name (which we expect is the unix</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* user name), and get the user's fullname (which we </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* expect will be in the format to pass back to</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* dsapi).</font></tt><br>
<tt><font size="2">		 */</font></tt><br>
<tt><font size="2">		if (0 == getUserNames (context,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(char *)authData-&gt;userName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;fullName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;fullNameLen,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;shortName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;shortNameLen) ) {</font></tt><br>
<tt><font size="2">			int unixauth;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Do the unix authentication. The </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* unixAuthenticate routine returns: -1 on</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* error, 0 on success, 1 if user is not known </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* to unix.</font></tt><br>
<tt><font size="2">			 */</font></tt><br>
<tt><font size="2">			unixauth = unixAuthenticate(shortName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (char *)authData-&gt;password);</font></tt><br>
<tt><font size="2">			/* Return if user is not known to unix */</font></tt><br>
<tt><font size="2">			if (1 == unixauth) {</font></tt><br>
<tt><font size="2">				printf(&quot;\nUser name not in UNIX system.\n&quot;)</font></tt><br>
<tt><font size="2">				return kFilterNotHandled;</font></tt><br>
<tt><font size="2">			} </font></tt><br>
<tt><font size="2">			/* Copy the canonical name for this user that</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* dsapi requires.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/</font></tt><br>
<tt><font size="2">			strncpy ((char *)authData-&gt;authName, fullName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;authData-&gt;authNameSize);</font></tt><br>
<br>
<tt><font size="2">			/* Fill in authType return info that dsapi</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* requires.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/</font></tt><br>
<tt><font size="2">			if (unixauth) {</font></tt><br>
<tt><font size="2">				/* The unixauthenticate routine</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* returned error: &nbsp;we couldn't</font></tt><br>
<tt><font size="2">				 * authenticate with the input</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* password.</font></tt><br>
<tt><font size="2">				 */</font></tt><br>
<tt><font size="2">				authData-&gt;authType = kNotAuthentic;</font></tt><br>
<tt><font size="2">			} else {</font></tt><br>
<tt><font size="2">				/* For debug purposes, write to the</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* Domino console that authentication</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* with the input password succeeded.</font></tt><br>
<tt><font size="2">				 * You may wish to remove this printf.</font></tt><br>
<tt><font size="2">				 */</font></tt><br>
<tt><font size="2">				printf(&quot;DSAPI Filter authenticated %s as %s (unix user %s)\n&quot;,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(char *)authData-&gt;userName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;authData-&gt;authName, shortName);</font></tt><br>
<tt><font size="2">				authData-&gt;authType = kAuthenticBasic;</font></tt><br>
<tt><font size="2">			}</font></tt><br>
<tt><font size="2">			return kFilterHandledEvent;</font></tt><br>
<tt><font size="2">		}</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">	return kFilterNotHandled;</font></tt><br>
<tt><font size="2">}</font></tt>
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b><font color="#000080">Actual routines to lookup the user from the Domino side.</font></b><br>
<br>
Each time this filter's Authenticate routine is called, a lookup will be done of the user in the Domino name and address book (assuming that the user is not found in the cache from a previous authentication). This lookup will attempt to retrieve the user's Domino  short name (e.g., jdoe) and the user's full Domino name. If unix user names do not correspond to Domino short names, this example would need to be changed to handle the way in which unix names should be mapped to Domino  names, and vice versa.  </td></tr>
</table>
<tt><font size="2">int getUserNames (FilterContext* context,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char *userName, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char **pUserFullName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; int &nbsp;*pUserFullNameLen,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char **pUserShortName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; int &nbsp;*pUserShortNameLen) {</font></tt><br>
<tt><font size="2">/*</font></tt><br>
<tt><font size="2">&nbsp;* Description: &nbsp;Lookup the user and return the user's full name and</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; short name.</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Input: &nbsp;context &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;context we'll use for allocating memory</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; userName &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; the name of the user to lookup</font></tt><br>
<tt><font size="2">&nbsp;* Output: pUserFullName &nbsp; &nbsp; &nbsp;location of the user's full name</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; pUserFullNameLen &nbsp; location to store the length of fullname</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; pUserShortName &nbsp; &nbsp; location of the user's shortname</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; pUserShortNameLen &nbsp;location to store the length of</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;shortname</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Return: -1 on error, 0 on success</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<tt><font size="2">	STATUS	error = NOERROR;</font></tt><br>
<tt><font size="2">	HANDLE	hLookup = NULLHANDLE;</font></tt><br>
<tt><font size="2">	WORD	Matches = 0;</font></tt><br>
<tt><font size="2">	char	*pLookup;</font></tt><br>
<tt><font size="2">	char	*pName = NULL;</font></tt><br>
<tt><font size="2">	char	*pMatch = NULL;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; int &nbsp; &nbsp; rc = -1;</font></tt><br>
<br>
<tt><font size="2">	if (!userName || !pUserFullName || !pUserFullNameLen || </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; !pUserShortName || !pUserShortNameLen)</font></tt><br>
<tt><font size="2">		return rc;</font></tt><br>
<br>
<tt><font size="2">	/* Initialize output */</font></tt><br>
<tt><font size="2">	*pUserFullName = NULL;</font></tt><br>
<tt><font size="2">	*pUserFullNameLen = 0;</font></tt><br>
<tt><font size="2">	*pUserShortName = NULL;</font></tt><br>
<tt><font size="2">	*pUserShortNameLen = 0;</font></tt><br>
<br>
<tt><font size="2">	/* do the name lookup</font></tt><br>
<tt><font size="2">	 */</font></tt><br>
<tt><font size="2">	error = NAMELookup(NULL, /* NULL means look locally */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0, &nbsp; /* flags */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;1, &nbsp; /* number of namespaces */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;$Users&quot;, /* namespace list */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;1, &nbsp; /* number of names to lookup */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;userName, /* list of names to lookup */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;2, /* number of items to return */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;FullName\0ShortName&quot;, /* list of items to</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* return */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;hLookup); /* place to receive handle of</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* return buffer */</font></tt><br>
<tt><font size="2">						</font></tt><br>
<tt><font size="2">	if (error || (NULLHANDLE == hLookup))</font></tt><br>
<tt><font size="2">		goto NoUnlockExit;</font></tt><br>
<br>
<tt><font size="2">	pLookup = (char *) OSLockObject(hLookup);</font></tt><br>
<tt><font size="2">		</font></tt><br>
<tt><font size="2">	/*	Get a pointer to our entry.</font></tt><br>
<tt><font size="2">	 */</font></tt><br>
<tt><font size="2">	pName = (char *)NAMELocateNextName(pLookup, /* name lookup</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* buffer */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULL, /* start at beginning of</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* lookup buffer */</font></tt><br>
<tt><font size="2">					&amp;Matches); /* Receives number</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; * of times we</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; * found the entry</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; * (should be 1)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">	/* If we didn't find the entry, then quit */</font></tt><br>
<tt><font size="2">	if ((pName == NULL) || (Matches &lt;= 0)) {</font></tt><br>
<tt><font size="2">		goto Exit;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">	</font></tt><br>
<tt><font size="2">	pMatch = (char *)NAMELocateNextMatch(pLookup, &nbsp;/* name lookup</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; * buffer */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pName, /* entry that we found */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULL); /* no previous match */</font></tt><br>
<tt><font size="2">	if (NULL == pMatch) {</font></tt><br>
<tt><font size="2">		goto Exit;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">	/* Get the full name from the info we got back */</font></tt><br>
<tt><font size="2">	if ( getLookupInfo (context,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pMatch,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pUserFullName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pUserFullNameLen) )</font></tt><br>
<tt><font size="2">		goto Exit;</font></tt><br>
<tt><font size="2">		</font></tt><br>
<tt><font size="2">	/* Get the short name from the info we got back */</font></tt><br>
<tt><font size="2">	if ( getLookupInfo (context,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pMatch,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 1,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pUserShortName,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pUserShortNameLen) )</font></tt><br>
<tt><font size="2">		goto Exit;</font></tt><br>
<tt><font size="2">	else</font></tt><br>
<tt><font size="2">		/* Success in all things */</font></tt><br>
<tt><font size="2">		rc = 0;</font></tt><br>
<br>
<tt><font size="2">Exit:</font></tt><br>
<tt><font size="2">	if ( pLookup &amp;&amp; hLookup )</font></tt><br>
<tt><font size="2">		OSUnlock(hLookup);</font></tt><br>
<tt><font size="2">NoUnlockExit:</font></tt><br>
<tt><font size="2">	if (NULLHANDLE != hLookup)</font></tt><br>
<tt><font size="2">		OSMemFree(hLookup);</font></tt><br>
<tt><font size="2">	return rc;</font></tt><br>
<tt><font size="2">}</font></tt><br>
<br>
<tt><font size="2">int getLookupInfo (FilterContext* context,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char *pMatch,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;int &nbsp;itemNumber,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char **pInfo,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;int &nbsp;*pInfoLen) {</font></tt><br>
<tt><font size="2">/*</font></tt><br>
<tt><font size="2">&nbsp;* Description: &nbsp;Get the info from the lookup buffer </font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Input: &nbsp;context &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;context we'll use for allocating memory</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; pMatch &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; the name of the lookup buffer</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; itemNumber &nbsp; &nbsp; &nbsp; &nbsp; where the info is stored in the lookup</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;buffer</font></tt><br>
<tt><font size="2">&nbsp;* Output: pInfo &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;location of the info buffer</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; pInfoLen &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; location to store the info length</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Return: -1 on error, 0 on success</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<br>
<tt><font size="2">	unsigned int reserved = 0;</font></tt><br>
<tt><font size="2">	unsigned int errID;</font></tt><br>
<tt><font size="2">	char	*ValuePtr = NULL;</font></tt><br>
<tt><font size="2">	WORD	ValueLength, DataType;</font></tt><br>
<tt><font size="2">	STATUS	error;</font></tt><br>
<tt><font size="2">	void	*newSpace = NULL;</font></tt><br>
<br>
<tt><font size="2">	if (!pMatch || !pInfo || !pInfoLen || (itemNumber &lt; 0))</font></tt><br>
<tt><font size="2">		return -1;</font></tt><br>
<br>
<tt><font size="2">	/* Initialize output */</font></tt><br>
<tt><font size="2">	*pInfo = NULL;</font></tt><br>
<tt><font size="2">	*pInfoLen = 0;</font></tt><br>
<br>
<tt><font size="2">	/* Check the type and length of the info */</font></tt><br>
<tt><font size="2">	ValuePtr = (char *)NAMELocateItem(pMatch, /* match that we</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* found */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; itemNumber, /* item # in order</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*of item on lookup */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;DataType, /* return the datatype</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; * of item value */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;ValueLength); /* size of rtn</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; * value */</font></tt><br>
<tt><font size="2">	if (NULL == ValuePtr || ValueLength == 0) {</font></tt><br>
<tt><font size="2">		/* there is no info */</font></tt><br>
<tt><font size="2">		return -1;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">	ValueLength -= sizeof(WORD); /* remove datatype word included </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; * in the list length </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */</font></tt><br>
<tt><font size="2">&nbsp;	/* check the value DataType */</font></tt><br>
<tt><font size="2">	switch (DataType) {</font></tt><br>
<tt><font size="2">		case TYPE_TEXT_LIST:</font></tt><br>
<tt><font size="2">			break;</font></tt><br>
<br>
<tt><font size="2">		case TYPE_TEXT:</font></tt><br>
<tt><font size="2">			break;</font></tt><br>
<br>
<tt><font size="2">		default:</font></tt><br>
<tt><font size="2">			return -1;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<br>
<tt><font size="2">	/* Allocate space for the info. &nbsp;This memory will be freed</font></tt><br>
<tt><font size="2">	 * automatically when the thread terminates.</font></tt><br>
<tt><font size="2">	 */</font></tt><br>
<tt><font size="2">	newSpace = (context-&gt;AllocMem)(context, ValueLength+1,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;reserved, &amp;errID);</font></tt><br>
<tt><font size="2">	*pInfo = (char *) newSpace;</font></tt><br>
<tt><font size="2">	if (NULL == *pInfo) {</font></tt><br>
<tt><font size="2">		printf (&quot;Out of memory\n&quot;);</font></tt><br>
<tt><font size="2">		return -1;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<br>
<tt><font size="2">	/* Get the info */</font></tt><br>
<tt><font size="2">	error = NAMEGetTextItem(pMatch, /* match that we found */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; itemNumber, /* item # in order of item</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* on lookup */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0, /* Member # of item in text</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; * lists */</font></tt><br>
<tt><font size="2">				*pInfo, /* buffer to copy result</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* into */</font></tt><br>
<tt><font size="2">				ValueLength+1); /* Length of buffer */</font></tt><br>
<tt><font size="2">	if (!error) {</font></tt><br>
<tt><font size="2">		*pInfoLen = ValueLength +1;</font></tt><br>
<tt><font size="2">		return 0;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">	return -1;</font></tt><br>
<tt><font size="2">}</font></tt><br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b><font color="#000080">Authenticate the user from the Unix side.</font></b></td></tr>
</table>
<br>
<tt><font size="2">int unixAuthenticate(char *userName, char *password) {</font></tt><br>
<tt><font size="2">/*</font></tt><br>
<tt><font size="2">&nbsp;* Description: &nbsp;See if the user is known to unix, and if so, check</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; that the password can be verified.</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Input: &nbsp;userName &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; unix user name</font></tt><br>
<tt><font size="2">&nbsp;* &nbsp; &nbsp; &nbsp; &nbsp; password &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; unix password</font></tt><br>
<tt><font size="2">&nbsp;*</font></tt><br>
<tt><font size="2">&nbsp;* Return: -1 on error, 0 on success, 1 if user is not known to unix</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<tt><font size="2">	char buffer[1024];</font></tt><br>
<tt><font size="2">	int error = -1;</font></tt><br>
<tt><font size="2">	int success = 0;</font></tt><br>
<tt><font size="2">	int unknown = 1;</font></tt><br>
<br>
<tt><font size="2">#ifdef AIX</font></tt><br>
<tt><font size="2">	struct passwd *result;</font></tt><br>
<tt><font size="2">#endif</font></tt><br>
<br>
<tt><font size="2">	printf(&quot;\nUserName = %s\n&quot;, *userName );</font></tt><br>
<tt><font size="2">	if (!userName)</font></tt><br>
<tt><font size="2">	{</font></tt><br>
<tt><font size="2">		printf(&quot;\nUserName = %s\n&quot;, *userName );</font></tt><br>
<tt><font size="2">		return error;</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<br>
<br>
<tt><font size="2">	/* Get the unix record for this user */</font></tt><br>
<br>
<tt><font size="2">#ifdef AIX</font></tt><br>
<tt><font size="2">	result = getpwnam(userName);</font></tt><br>
<tt><font size="2">	if (result &amp;&amp; result-&gt;pw_passwd) {</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Encrypt the password and see if it matches the </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* encrypted password from the user's record.</font></tt><br>
<tt><font size="2">		 */</font></tt><br>
<tt><font size="2">		char *thisCrypt = NULL;</font></tt><br>
<tt><font size="2">		thisCrypt = (char *)crypt(password,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; result-&gt;pw_passwd);</font></tt><br>
<tt><font size="2">		if (strcmp (result-&gt;pw_passwd, thisCrypt) == 0) {</font></tt><br>
<tt><font size="2">			return success;</font></tt><br>
<tt><font size="2">		} else {</font></tt><br>
<tt><font size="2">			return error;</font></tt><br>
<tt><font size="2">		}</font></tt><br>
<tt><font size="2">	}</font></tt><br>
<tt><font size="2">#endif</font></tt><br>
<tt><font size="2">	return unknown;</font></tt><br>
<tt><font size="2">}</font></tt><br>
<br>
<tt><font size="2">/* ----- end of dsapifilter.c */</font></tt><br>

---
