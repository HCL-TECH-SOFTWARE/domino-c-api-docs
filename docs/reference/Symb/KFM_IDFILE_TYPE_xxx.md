##### Symbolic Value : User Registration
##### KFM_IDFILE_TYPE_xxx - Various types of IDs that can be created.
---
```
#include <kfm.h>
```

**Symbolic Values :**

	KFM_IDFILE_TYPE_FLAT	  -  Flat name space (V2 compatible)

	KFM_IDFILE_TYPE_STD	  -  Standard (user/server hierarchical)

	KFM_IDFILE_TYPE_ORG	  -  Organization certifier

	KFM_IDFILE_TYPE_ORGUNIT	  -  Organizational unit certifier

	KFM_IDFILE_TYPE_DERIVED	  -  Derived from certifer context. (hierarchical => STD; non-hierarchical => FLAT)

	KFM_IDFILE_TYPE_INET	  -  Internet certifier.


**Description :**

Constants used to indicate various types of IDs that can be created.


**See Also :**
[REGNewCertifier](/domino-c-api-docs/reference/Func/REGNewCertifier)
[REGNewServer](/domino-c-api-docs/reference/Func/REGNewServer)
[REGNewServerExtended](/domino-c-api-docs/reference/Func/REGNewServerExtended)
[REGNewWorkstation](/domino-c-api-docs/reference/Func/REGNewWorkstation)
[REGNewWorkstationExtended](/domino-c-api-docs/reference/Func/REGNewWorkstationExtended)
---
