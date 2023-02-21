##### Data Type : DSAPI
##### ServerSupportTypes - DSAPI Server support function types.
---
```
#include <dsapi.h>
```
**Description :**

Server support function types can be specified within the ServerSupport 
functionality defined within a FilterContext for a DSAPI filter. 

funcType indicates the service to be performed. Possible values are:
kWriteResponseHeaders - Write response status code, reason text, and headers to 
the client.
kOwnsRequest - Claims ownership of the http request. Only the filter that 
claims ownership of the request will get notified of events from then on 
forward, and only the filter (no default processing of the request) is to 
process the request, i.e, the filter better be prepared to handle the event 
kFilterProcessRequest and generate the response data for the client.
kGetParsedRequest - Retreives the components of the parsed request.
kWrite102Processing - 
kGetAuthenticatedUserInfo - Get the authenticated user information including 
his/her web user name, password, group list, cannonical user name... Note that 
this service is only valid after the authentication phase has taken place for 
web user name, password, and cannonical name (the web user name and password 
will not be available before authentication has taken place in the case of 
session authentication.) The user's group list will not be available until the 
user's group list generation phase has taken place.

**See Also :**
[FilterAuthenticatedUser](/domino-c-api-docs/reference/Data/FilterAuthenticatedUser)
[FilterContext](/domino-c-api-docs/reference/Data/FilterContext)
[FilterParsedRequestLine](/domino-c-api-docs/reference/Data/FilterParsedRequestLine)
[FilterResponseHeaders](/domino-c-api-docs/reference/Data/FilterResponseHeaders)
---
