##### Data Type : DSAPI
##### FilterParsedRequestLine - Data1 for DSAPI server support function kGetParsedRequest
---
```
#include <dsapi.h>
```
**Description :**

The FilterParsedRequestLine structure is used by the ServerSupport callback 
functionality of the FilterContext.  see FilterContext for more information

pRawUri - (Input)  Pointer to the raw uri from the input request line.
pPathUri - (Input)  Pointer to the path uri in the input request line.
pQueryUri - (Input)  Pointer to the query string from the input request line.
pFragmentUri - 
pSchemeUri - 
pHostInfoUri - (Input)  Pointer to the part with the host name in the url.
pHostName - (Input)  Pointer to the host name after we have parsed the request 
line.
hostPort - (Input)  The host port number the request came in.
pUserUri - (Input)  Pointer to the user name from the input request line. It is 
set to NULL is none is provided.
pUserPasswordUri - (Input)  Pointer to the user's password from the request 
input line. it is set to NULL if none was provided.
majorProtocolVersion - (Input)  The major version number of the http protocol 
used for the request.
minorProtocolVersion - (Input)  The minor version number of the http protocol 
used for the request.


**See Also :**
[FilterContext](/domino-c-api-docs/reference/Data/FilterContext)
[ServerSupportTypes](/domino-c-api-docs/reference/Data/ServerSupportTypes)
---
