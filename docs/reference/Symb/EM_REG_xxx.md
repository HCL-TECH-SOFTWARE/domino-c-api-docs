##### Symbolic Value : Extension Manager
##### EM_REG_xxx - EMRegister() option flags
---
```
#include <extmgr.h>
```

**Symbolic Values :**

	EM_REG_BEFORE	  -  Call the hook before Domino or Notes core operation.

	EM_REG_AFTER	  -  Call the hook after Domino or Notes core operation.


**Description :**

These flag values are passed to EMRegister() to indicate whether the callback function is to be called before or after Domino or Notes completes the core processing for this operation.  These two flags may be combined to indicate that the callback should be called both before and after core processing.


**See Also :**
[EMRegister](/domino-c-api-docs/reference/Func/EMRegister)
---
