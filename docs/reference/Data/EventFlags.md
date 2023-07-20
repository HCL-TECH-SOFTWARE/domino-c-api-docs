##### Data Type : DSAPI
##### EventFlags - DSAPI Defined events for a filter.
---
```
#include <dsapi.h>
```

**Definition :**
```
typedef enum {
	kFilterRawRequest  = 0x01,
 kFilterParsedRequest = 0x02,
 kFilterAuthUser  = 0x04,
 kFilterUserNameList = 0x08,
 kFilterMapURL  = 0x10,
	 kFilterResponse  = 0x20,
	kFilterRawWrite  = 0x40,
 kFilterEndRequest  = 0x80,
 kFilterStartRequest = 0x100,
 kFilterPostTranslate = 0x200,
 kFilterAuthorized  = 0x400,
 kFilterProcessRequest = 0x800,
 kFilterAuthenticate = 0x2000,
 kFilterRewriteURL  = 0x4000,

	kFilterAny   = 0x6FFF & ~kFilterAuthUser  /*  */
} EventFlags;
#define kFilterTranslateRequest 0x10 /* Same as kFilterMapURL event. */
```

**Description :**

EventFlags indicate for which event(s) the filter will act upon.  The events can be OR'ed to specifiy more than one event.
<ul><br>
<br>
kFilterRawRequest	- Notification that the input headers for a request are ready for processing.<br>
kFilterParsedRequest	- Notification the input http headers have been parsed and are available.<br>
kFilterAuthUser	- Backward compatibility of authentication and authorizing a web user. For new filters, use the kFilterAuthenticate and kFilterAuthorized events instead.<br>
kFilterUserNameList	- Notification that the user's group list is about to be computed. Filters can override the default implementation of user's group list generation.<br>
kFilterMapURL	- Notification that a request is about to be translated to a resource.  (Note that kFilterTranslateRequest is equivalent to kFilterMapURL)</ul>
	kFilterResponse	  	- Notification that the headers for a response are about to be sent to the client. A filter that supports this event can 					  change the response given to the user for a given request.<br>
	kFilterRawWrite		- <font face="Symbol"> </font>Notification that a response data buffer is about to be sent to the client. A filter supporting this event can change the 				  data before it is sent.
<ul>kFilterEndRequest	- Notification that the servicing of an http request is finished. It is now time to clean up and release any global resources the filter is holding.<br>
kFilterStartRequest	- Notification that we are about to start servicing a new http request.<br>
kFilterPostTranslate	- Notification that a request has been translated. A filter could change which resource we are about to access.<br>
kFilterAuthorized	- Notification that the authorization phase is about to take place. A filter can override the default authorization implementation by supporting this event.<br>
kFilterProcessRequest	- Notification that we are about to process the request after all previous steps have taken place. A filter can override the default implementation of servicing some request by supporting this event.<br>
kFilterAuthenticate	- Notification that the authentication phase is about to start. Filters can override the default implementation of authentication by supporting this event.<br>
kFilterRewriteURL	- Notification to change the original URL. A filter might choose to change the original URL.<br>
kFilterAny	- All event types<br>
</ul>
<b>	</b>kFilterTranslateRequest          - This is equivalent to the kFilterMapURL event flag
<ul><br>
See the chapter, Domino Web Server Application Interface (DSAPI), in the <i>Lotus C API User Guide</i> for details.</ul>



**See Also :**
[FilterAuthenticate](/domino-c-api-docs/reference/Data/FilterAuthenticate)
[FilterInitData](/domino-c-api-docs/reference/Data/FilterInitData)
[FilterUserNameList](/domino-c-api-docs/reference/Data/FilterUserNameList)
---
