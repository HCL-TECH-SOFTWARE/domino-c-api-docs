##### Data Type : DSAPI
##### FilterRequest - DSAPI Request information within a FilterContext
---
```
#include <dsapi.h>
```

**Definition :**
```
typedef struct {
   unsigned int   method;
   char*          URL;
   char*          version;
   char*          userName;
   char*          password;
   unsigned char* clientCert;
   unsigned int   clientCertLen;
   char*          contentRead;
   unsigned int   contentReadLen;
} FilterRequest;
```

**Description :**

A GetRequest within a FilterContext can be called to retrieve request line (first line of request) information and reports on other information as the request is processed. The first line of an HTTP request has this syntax: &lt;method&gt; &lt;url&gt; &lt;version&gt;. For example, &quot;GET /sales.nsf?OpenDatabase HTTP/1.0&quot;.
<ul><br>
<br>
method	- The type of HTTP request, see RequestMethod<br>
URL	- The &lt;url&gt; part of the request line.<br>
version	- The &lt;version&gt; part of the http protocol.<br>
userName	- The user's web name or NULL if not present.<br>
password	- The user's web password or NULL, if not present.<br>
clientCert	- The user's SSL client certificate or NULL if not present.<br>
clientCertLen	- The number of bytes in the user's SSL client certificate, or 0 if not present.<br>
contentRead	- The buffer containing the post data already read, NULL is no post data has been read.<br>
contentReadLen	- The number of bytes of post data available, 0 if none is present.<br>
</ul>



**See Also :**
[FilterContext](/domino-c-api-docs/reference/Data/FilterContext)
[RequestMethod](/domino-c-api-docs/reference/Data/RequestMethod)
---
