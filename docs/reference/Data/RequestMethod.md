##### Data Type : DSAPI
##### RequestMethod - DSAPI  Incoming HTTP request
---
```
#include <dsapi.h>
```

**Definition :**
```
typedef enum {
	kRequestNone = 0,
 kRequestHEAD = 1,
 kRequestGET = 2,
 kRequestPOST = 3,
 kRequestPUT = 4,
 kRequestDELETE = 5,
 kRequestTRACE = 6,
 kRequestCONNECT = 7,
 kRequestOPTIONS = 8,
 kRequestUNKNOWN = 9,
 kRequestBAD = 10
} RequestMethod;

```

**Description :**

This structure defines the supported HTTP Request Methods within a FilterRequest.  
<ul><br>
<br>
kRequestNone	- No HTTP request method is provided.<br>
kRequestHEAD	- method is often used for testing hypertext links for validity, accessibility, and recent modification<br>
kRequestGET	- GET method - used to retrieve whatever information (in the form of an entity) is identified by the Request-URL<br>
kRequestPOST	- POST method - requests that the origin server accept the entity enclosed in the request as a new subordinate of the resource identified by the Request-URL in the Request-Line<br>
kRequestPUT	- PUT method - requests that the enclosed entity be stored under the supplied Request-URL<br>
kRequestDELETE	- DELETE method - requests that the origin server delete the resource identified by the Request-URL<br>
kRequestTRACE	- TRACE method<br>
kRequestCONNECT	- CONNECT method<br>
kRequestOPTIONS	- OPTIONS method<br>
kRequestUNKNOWN	- Unknown request method.<br>
kRequestBAD	- Bad request method. Error.</ul>



**See Also :**
[FilterRequest](/domino-c-api-docs/reference/Data/FilterRequest)
---
