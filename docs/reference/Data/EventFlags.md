##### Data Type : DSAPI
##### EventFlags - DSAPI Defined events for a filter.
---
```
#include <dsapi.h>
```
**Description :**

EventFlags indicate for which event(s) the filter will act upon.  The events 
can be OR'ed to specifiy more than one event.

kFilterRawRequest - Notification that the input headers for a request are ready 
for processing.
kFilterParsedRequest - Notification the input http headers have been parsed and 
are available.
kFilterAuthUser - Backward compatibility of authentication and authorizing a 
web user. For new filters, use the kFilterAuthenticate and kFilterAuthorized 
events instead.
kFilterUserNameList - Notification that the user's group list is about to be 
computed. Filters can override the default implementation of user's group list 
generation.
kFilterMapURL - Notification that a request is about to be translated to a 
resource.  (Note that kFilterTranslateRequest is equivalent to kFilterMapURL)
	kFilterResponse    - Notification that the headers for a response are 
about to be sent to the client. A filter that supports this event can        
change the response given to the user for a given request.
	kFilterRawWrite  -  Notification that a response data buffer is about 
to be sent to the client. A filter supporting this event can change the       
data before it is sent.
kFilterEndRequest - Notification that the servicing of an http request is 
finished. It is now time to clean up and release any global resources the 
filter is holding.
kFilterStartRequest - Notification that we are about to start servicing a new 
http request.
kFilterPostTranslate - Notification that a request has been translated. A 
filter could change which resource we are about to access.
kFilterAuthorized - Notification that the authorization phase is about to take 
place. A filter can override the default authorization implementation by 
supporting this event.
kFilterProcessRequest - Notification that we are about to process the request 
after all previous steps have taken place. A filter can override the default 
implementation of servicing some request by supporting this event.
kFilterAuthenticate - Notification that the authentication phase is about to 
start. Filters can override the default implementation of authentication by 
supporting this event.
kFilterRewriteURL - Notification to change the original URL. A filter might 
choose to change the original URL.
kFilterAny - All event types

	kFilterTranslateRequest          - This is equivalent to the 
kFilterMapURL event flag

See the chapter, Domino Web Server Application Interface (DSAPI), in the Lotus 
C API User Guide for details.

**See Also :**
[FilterAuthenticate](/reference/Data/FilterAuthenticate)
[FilterInitData](/reference/Data/FilterInitData)
[FilterUserNameList](/reference/Data/FilterUserNameList)
---
