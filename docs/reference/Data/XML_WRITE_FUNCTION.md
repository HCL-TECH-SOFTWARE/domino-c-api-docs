##### Data Type : XML
##### XML_WRITE_FUNCTION - XML write function
---
```
#include <xml.h>
```

**Definition :**

typedef void (LNCALLBACKPTR XML_WRITE_FUNCTION) (const BYTE *pBuffer, DWORD 
length, void far *pAction );

**Description :**

This is the datatype of the Callback function passed to DXLExportACL, DXLExportDatabase, DXLExportNote and DXLExportIDTable and XSLTTransform..


**See Also :**
[DXLExportACL](/domino-c-api-docs/reference/Func/DXLExportACL)
[DXLExportDatabase](/domino-c-api-docs/reference/Func/DXLExportDatabase)
[DXLExportIDTable](/domino-c-api-docs/reference/Func/DXLExportIDTable)
[DXLExportNote](/domino-c-api-docs/reference/Func/DXLExportNote)
[XSLTTransform](/domino-c-api-docs/reference/Func/XSLTTransform)
---
