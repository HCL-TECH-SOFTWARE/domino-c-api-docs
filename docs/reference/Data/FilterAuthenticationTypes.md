##### Data Type : DSAPI
##### FilterAuthenticationTypes - DSAPI FilterAuthenticate authType
---
```
#include <dsapi.h>
```

**Definition :**
```
typedef enum {
   kNotAuthentic         = 0,
   kAuthenticBasic       = 1,
   kAuthenticClientCert  = 2
} FilterAuthenticationTypes;
```

**Description :**

The type of authorization.  If the filter handles this event, the filter must set authType within the FilterAuthenticate structure to one of these values.
<ul><br>
<br>
kNotAuthentic	- User's credentials failed authentication. The http stack must terminate the processing of the request. <br>
kAuthenticBasic	- User's name and password has passed authentication. The authentication phase should be terminated, and the next phase in the processing of the request started.<br>
kAuthenticClientCert	- The SSL authentication using an SSL client certificate has succeeded. The authentication phase should be terminated, and the next phase in the processing of the request started.</ul>



**See Also :**
[FilterAuthenticate](/domino-c-api-docs/reference/Data/FilterAuthenticate)
---
