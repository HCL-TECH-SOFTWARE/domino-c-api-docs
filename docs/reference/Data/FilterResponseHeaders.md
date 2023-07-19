##### Data Type : DSAPI
##### FilterResponseHeaders - DSAPI FilterContext / ServerSupport Filter Response Headers
---
```
#include <dsapi.h>
```

**Definition :**

typedef struct {
   unsigned int   responseCode;
   char*          reasonText;
   char*          headerText;
} FilterResponseHeaders;

**Description :**

The FilterResponseHeaders structure is used by the ServerSupport callback functionality of the FilterContext.  see FilterContext for more information.<br>

<ul>responseCode	- (Output)  Set to the http status code to send back to the client.<br>
reasonText		- (Output)  Set to the reason response text to add to the response line. It can be set to NULL if none is available.<br>
headerText		- (Output)  Points to a buffer of response http headers to append to the default response headers if any. Can be set to NULL, if no headers are to be appended. If not NULL, each header must be terminated by a carriage return and line feed characters (&quot;\r\n&quot;), and the whole sequence of headers must end with two &quot;\r\n&quot; sequence.</ul>



**See Also :**
[FilterContext](/domino-c-api-docs/reference/Data/FilterContext)
[ServerSupportTypes](/domino-c-api-docs/reference/Data/ServerSupportTypes)
---
