##### Data Type : XML
##### DXLLOGOPTION - DXL Import Options for log reporting
---
```
#include <xml.h>
```

**Definition :**

typedef enum
{
	DXLLOGOPTION_IGNORE=1,  /* ignore the action.  don't log anything and 
just continue */
	DXLLOGOPTION_WARNING=2,  /* log the problem as a warning */
	DXLLOGOPTION_ERROR=3,  /* log the problem as an error */
	DXLLOGOPTION_FATALERROR=4  /* log the problem as a fatal error */

} DXLLOGOPTION; 

**Description :**

Values to set DXL_IMPORT_PROPERTY member iUnknownTokenLogOption.  


**See Also :**
[DXLGetImporterProperty](/domino-c-api-docs/reference/Func/DXLGetImporterProperty)
[DXLSetImporterProperty](/domino-c-api-docs/reference/Func/DXLSetImporterProperty)
[DXL_IMPORT_PROPERTY](/domino-c-api-docs/reference/Data/DXL_IMPORT_PROPERTY)
---
