##### Data Type : Billing
##### HTTPREQREC - Http Request Record
---
```
#include <billing.h>
```

**Definition :**

typedef struct {
   DWORD HttpContentLength;     /* Content Length send/received
                                   to/from client */
   DWORD HttpReqTimeMs;         /* Number of milliseconds to
                                   process request */
   DWORD HttpStatusCode;        /* Status code returned by the
                                   server */
   WORD  HttpTimeStampOffset;   /* Offset to http time stamp in a
                                   string format */
   WORD  HttpAuthUserOffset;    /* Offset to Authenticated User
                                   string */
   WORD  HttpPartnerOffset;     /* Offset to remote machine name
                                   string */
   WORD  HttpRefererOffset;     /* Offset to refering URL string */
   WORD  HttpServerAddrOffset;  /* Offset to connection IP address */
   WORD  HttpUserAgentOffset;   /* Offset to user agent string */
   WORD  HttpRequestLineOffset; /* Offset to Request line string */
   WORD  HttpContentTypeOffset; /* Offset to content type string */
/* Time Stamp, AuthUser, Partner and other strings follow */
} HTTPREQREC;

**Description :**

To create Http Request billing records you must include the HttpRequest keyword in the notes.ini BillingClass variable on the billing server.  This enables the server to write http request-related information to the billing message queue which can then be read to the HTTPREQREC structure by the billing server task.
<ul><br>
<br>
For more information about billing for Domino agents, see<i> </i><i>Domino 5 Administration Help</i><i>.</i><br>
<br>
<b><u>Structure Description</u></b><br>
<br>
<b>HttpContentLength</b> -- Length of string representing content sent to/received from client<br>
<br>
<b>HttpReqTimeMS</b> -- Number fo milliseconds to process request<br>
<br>
<b>HttpStatusCode</b> -- Status code returned by the server<br>
<br>
<b>HttpTimeStampOffset</b> -- Offset to http timestamp string<br>
<br>
<b>HttpAuthUserOffset</b> -- Offset to Authenticated user string<br>
<br>
<b>HttpPartnerOffset</b> -- Offset to remote machine name string<br>
<br>
<b>HttpRefererOffset</b> -- Offset to refering URL string<br>
<br>
<b>HttpServerAddrOffset</b> -- Offset to connection IP address string<br>
<br>
<b>HttpUserAgentOffset</b> -- Offset to user agent string<br>
<br>
<b>HttpRequestLineOffset</b> -- Offset to Request line string<br>
<br>
<b>HttpContentTypeOffset</b> -- Offset to content type string<br>
<br>
Note: All offset members are relative to the beginning of the record (&amp;HttpContentLength), if an offset member is set to 0 the member is not available.</ul>



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
