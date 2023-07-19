##### Data Type : DSAPI
##### FilterParsedRequestLine - Data1 for DSAPI server support function kGetParsedRequest
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct{
 char *pRawUri;
 char *pPathUri;
 char *pQueryUri;
 char *pFragmentUri;
	char *pSchemeUri;
 char *pHostInfoUri;
 char *pHostName;
 int hostPort;
	char *pUserUri;
 char *pUserPasswordUri;
	int majorProtocolVersion;
 int minorProtocolVersion;
}FilterParsedRequestLine;

**Description :**

The FilterParsedRequestLine structure is used by the ServerSupport callback functionality of the FilterContext.  see FilterContext for more information<br>

<ul>pRawUri	- (Input)  Pointer to the raw uri from the input request line.<br>
pPathUri	- (Input)  Pointer to the path uri in the input request line.<br>
pQueryUri	- (Input)  Pointer to the query string from the input request line.<br>
pFragmentUri	- <br>
pSchemeUri	- <br>
pHostInfoUri	- (Input)  Pointer to the part with the host name in the url.<br>
pHostName	- (Input)  Pointer to the host name after we have parsed the request line.<br>
hostPort	- (Input)  The host port number the request came in.<br>
pUserUri	- (Input)  Pointer to the user name from the input request line. It is set to NULL is none is provided.<br>
pUserPasswordUri	- (Input)  Pointer to the user's password from the request input line. it is set to NULL if none was provided.<br>
majorProtocolVersion	- (Input)  The major version number of the http protocol used for the request.<br>
minorProtocolVersion	- (Input)  The minor version number of the http protocol used for the request.</ul>



**See Also :**
[FilterContext](/domino-c-api-docs/reference/Data/FilterContext)
[ServerSupportTypes](/domino-c-api-docs/reference/Data/ServerSupportTypes)
---
