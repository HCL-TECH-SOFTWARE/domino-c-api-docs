##### Symbolic Value : Extension Manager
##### fAuth_xxx - Authentication Extension Manager flags
---
```
#include <extmgr.h>
```

**Symbolic Values :**

	fAuthRoleServer	  -  This flag is set to indicate that the callback is being called during authentication in the role of the server.

	fAuthRolePassthruServer	  -  This flag is set when the client is authenticating with the server with the intention of using the server as a passthru server.

	fAuthClientViaPassthruServer	  -  This flag is set when the client is accessing the server thru a passthru server. The network address in this case is the address of the passthru server ( not the client).


**Description :**

Authentication Extension Manager flags that indicate details of authentication role and state.


**See Also :**
[AUTHEM_xxx](/domino-c-api-docs/reference/Symb/AUTHEM_xxx)
[AuthenticationEMCallback](/domino-c-api-docs/reference/Func/AuthenticationEMCallback)
[EM_xxx](/domino-c-api-docs/reference/Symb/EM_xxx)
---
