##### Data Type : XML
##### XML_READ_FUNCTION - XML read function
---
```
#include <xml.h>
```

**Definition :**

typedef DWORD (LNCALLBACKPTR XML_READ_FUNCTION) (BYTE *pBuffer, DWORD length, 
void far *pAction);

**Description :**

This is the datatype of the Callback function passed to functions DXLImport and XSLTTransform.


**See Also :**
[DXLImport](/domino-c-api-docs/reference/Func/DXLImport)
[XSLTTransform](/domino-c-api-docs/reference/Func/XSLTTransform)
---
