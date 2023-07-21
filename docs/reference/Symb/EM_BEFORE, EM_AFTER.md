##### Symbolic Value : Extension Manager
##### EM_BEFORE, EM_AFTER - EMRECORD - NotificationType
---
```
#include <extmgr.h>
```

**Symbolic Values :**

	EM_BEFORE	  -  Call is before Domino or Notes core processing.

	EM_AFTER	  -  Call is after Domino or Notes core processing.


**Description :**

Indicator stored in the EMRECORD passed to an extension manager callback.  This value tells the callback whether this call is before or after Domino or Notes has performed the core processing for this operation.


**See Also :**
[EMRECORD](/domino-c-api-docs/reference/Data/EMRECORD)
---
