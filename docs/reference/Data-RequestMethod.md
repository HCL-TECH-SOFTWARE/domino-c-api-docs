##### Data Type : DSAPI
##### RequestMethod - DSAPI  Incoming HTTP request
---
##### #include <dsapi.h>
**Description :**
This structure defines the supported HTTP Request Methods within a 
FilterRequest.  

kRequestNone - No HTTP request method is provided.
kRequestHEAD	- method is often used for testing hypertext links for 
validity, accessibility, and recent modification
kRequestGET - GET method - used to retrieve whatever information (in the form 
of an entity) is identified by the Request-URL
kRequestPOST - POST method - requests that the origin server accept the entity 
enclosed in the request as a new subordinate of the resource identified by the 
Request-URL in the Request-Line
kRequestPUT - PUT method - requests that the enclosed entity be stored under 
the supplied Request-URL
kRequestDELETE	- DELETE method - requests that the origin server delete 
the resource identified by the Request-URL
kRequestTRACE	- TRACE method
kRequestCONNECT	- CONNECT method
kRequestOPTIONS	- OPTIONS method
kRequestUNKNOWN - Unknown request method.
kRequestBAD - Bad request method. Error.
**See Also :**
[FilterRequest](D:/md_files/FilterRequest.md)
---
