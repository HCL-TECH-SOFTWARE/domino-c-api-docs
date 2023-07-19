##### Data Type : DSAPI
##### FilterAuthConfigFlags - DSAPI FilterAuthenticate authFlags
---
```
#include <dsapi.h>
```

**Definition :**

typedef enum {
   kAuthAllowBasic         = 1,
   kAuthAllowAnonymous     = 2,
   kAuthAllowSSLCert       = 4,
   kAuthAllowSSLBasic      = 8,
   kAuthAllowSSLAnonymous  = 16,
   kAuthRedirectToSSL      = 32
} FilterAuthConfigFlags;

**Description :**

The authentication options enabled for the server.  The values for a server can be found under the Internet Ports section within the server document.  The values can be added together.
<ul><br>
<br>
kAuthAllowBasic	- The server allows basic authentication by providing a user name and password.<br>
kAuthAllowAnonymous	- The server allows anonymous access to public (non protected) documents.<br>
kAuthAllowSSLCert	- The server allows SSL authentication using an SSL client certificate.<br>
kAuthAllowSSLBasic	- The server allows SSL authentication by providing a user name and password.<br>
kAuthAllowSSLAnonymous	- The server allows anonymous SSL authentication to public (non protected) documents.<br>
kAuthRedirectToSSL	- The server allows redirections to SSL authentication for documents that are SSL protected.</ul>



**See Also :**
[FilterAuthenticate](/domino-c-api-docs/reference/Data/FilterAuthenticate)
---
