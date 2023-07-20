##### Symbolic Value : Constants
##### AUTHEM_xxx - Authentication Extension Manager events
---
```
#include <extmgr.h>
```

**Symbolic Values :**

	AUTHEM_StartAuthentication	  -  An EM_SECAUTHENTICATION wEvent calling parameter indicating the callback should initiate it's additional authentication protocol - WORD (0x0000).

	AUTHEM_Poll	  -  An EM_SECAUTHENTICATION wEvent calling parameter indicating the callback has been invoked again after a delay for additional processing - WORD (0x0001).

	AUTHEM_Identify	  -  An EM_SECAUTHENTICATION wEvent calling parameter indicating the first authentication of the registered Extension Manager callback. This callback expects a uniquely labeled null terminated text string to be returned in the pName parameter that identifies the 3rd party authentication extension - WORD (0x0002).

	AUTHEM_Terminate	  -  An EM_SECAUTHENTICATION wEvent calling parameter indicating the session is closing and may have failed - WORD (0x0003).


**Description :**

The Authentication Extension Manager EM_SECAUTHENTICATION wEvent calling parameters.


**See Also :**
[AuthenticationEMCallback](/domino-c-api-docs/reference/Func/AuthenticationEMCallback)
[EM_xxx](/domino-c-api-docs/reference/Symb/EM_xxx)
[fAuth_xxx](/domino-c-api-docs/reference/Symb/fAuth_xxx)
---
