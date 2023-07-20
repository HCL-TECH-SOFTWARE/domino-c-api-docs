##### Symbolic Value : Domino Upgrade Services
##### DUS_ERROR_LEVEL_xxx - For extended error processing. Used in pErrorLevel param with DUSExtendedErrorText.
---
```
#include <dus.h>
```

**Symbolic Values :**

	DUS_ERROR_LEVEL_INFO	  -  DUS application declaring an informational error only.

	DUS_ERROR_LEVEL_WARNING	  -  DUS application declaring a warning message only.

	DUS_ERROR_LEVEL_ERROR	  -  DUS application declaring a fatal error which will signify the DUS framework to shutdown the DUS application gracefully.

	DUS_ERROR_NO_DISPLAY	  -  Use this flag if the error should not be displayed.


**Description :**




**See Also :**
[DUSExtendedErrorText](/domino-c-api-docs/reference/Func/DUSExtendedErrorText)
---
