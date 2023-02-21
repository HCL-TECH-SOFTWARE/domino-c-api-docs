##### Data Type : DSAPI
##### FilterRequest - DSAPI Request information within a FilterContext
---
```
#include <dsapi.h>
```
**Description :**

A GetRequest within a FilterContext can be called to retrieve request line 
(first line of request) information and reports on other information as the 
request is processed. The first line of an HTTP request has this syntax: 
<method> <url> <version>. For example, "GET /sales.nsf?OpenDatabase HTTP/1.0".

method - The type of HTTP request, see RequestMethod
URL - The <url> part of the request line.
version - The <version> part of the http protocol.
userName - The user's web name or NULL if not present.
password - The user's web password or NULL, if not present.
clientCert - The user's SSL client certificate or NULL if not present.
clientCertLen - The number of bytes in the user's SSL client certificate, or 0 
if not present.
contentRead - The buffer containing the post data already read, NULL is no post 
data has been read.
contentReadLen - The number of bytes of post data available, 0 if none is 
present.



**See Also :**
[FilterContext](/domino-c-api-docs/reference/Data/FilterContext)
[RequestMethod](/domino-c-api-docs/reference/Data/RequestMethod)
---
