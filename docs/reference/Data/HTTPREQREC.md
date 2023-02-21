##### Data Type : Billing
##### HTTPREQREC - Http Request Record
---
```
#include <billing.h>
```
**Description :**

To create Http Request billing records you must include the HttpRequest keyword 
in the notes.ini BillingClass variable on the billing server.  This enables the 
server to write http request-related information to the billing message queue 
which can then be read to the HTTPREQREC structure by the billing server task.

For more information about billing for Domino agents, see Domino 5 
Administration Help.

Structure Description

HttpContentLength -- Length of string representing content sent to/received 
from client

HttpReqTimeMS -- Number fo milliseconds to process request

HttpStatusCode -- Status code returned by the server

HttpTimeStampOffset -- Offset to http timestamp string

HttpAuthUserOffset -- Offset to Authenticated user string

HttpPartnerOffset -- Offset to remote machine name string

HttpRefererOffset -- Offset to refering URL string

HttpServerAddrOffset -- Offset to connection IP address string

HttpUserAgentOffset -- Offset to user agent string

HttpRequestLineOffset -- Offset to Request line string

HttpContentTypeOffset -- Offset to content type string

Note: All offset members are relative to the beginning of the record 
(&HttpContentLength), if an offset member is set to 0 the member is not 
available.

**See Also :**
[AGENTREC](/domino-c-api-docs/reference/Data/AGENTREC)
[BILLMSG](/domino-c-api-docs/reference/Data/BILLMSG)
[BILLREC](/domino-c-api-docs/reference/Data/BILLREC)
[DBREC](/domino-c-api-docs/reference/Data/DBREC)
[DOCUMENT](/domino-c-api-docs/reference/Data/DOCUMENT)
[MAILREC](/domino-c-api-docs/reference/Data/MAILREC)
[REPLREC](/domino-c-api-docs/reference/Data/REPLREC)
[SESSIONREC](/domino-c-api-docs/reference/Data/SESSIONREC)
---
