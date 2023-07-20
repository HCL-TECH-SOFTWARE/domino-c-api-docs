##### Symbolic Value : Agents
##### ASSISTODS_FLAG_xxx - Agent control flags.
---
```
#include <queryods.h>
```

**Symbolic Values :**

	ASSISTODS_FLAG_HIDDEN	  -  TRUE if manual assistant is hidden.

	ASSISTODS_FLAG_NOWEEKENDS	  -  Do not run on weekends.

	ASSISTODS_FLAG_STOREHIGHLIGHTS	  -  TRUE if storing highlights.

	ASSISTODS_FLAG_MAILANDPASTE	  -  TRUE if this is the V3-style mail and paste macro.

	ASSISTODS_FLAG_CHOOSEWHENENABLED	  -  TRUE if server to run on should be chosed when enabled.


**Description :**

These flags are set in the dwFlags field of the ODS_ASSISTSTRUCT record.


**See Also :**
[ODS_ASSISTSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTSTRUCT)
---
