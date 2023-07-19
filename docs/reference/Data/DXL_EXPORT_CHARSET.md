##### Data Type : XML
##### DXL_EXPORT_CHARSET - DXL export charset
---
```
#include <xml.h>
```

**Definition :**

typedef enum
{
	eDxlExportUtf8,   /* (default) "encoding =" attribute is set to utf8 
and output charset is utf8 */
	eDxlExportUtf16   /* "encoding =" attribute is set to utf16 and charset 
is utf16 */

} DXL_EXPORT_CHARSET;

**Description :**

Values to set DXL_EXPORT_PROPERTY member eDxlExportCharset.  Default value is eDxlExportUtf8.


**See Also :**
[DXL_EXPORT_PROPERTY](/domino-c-api-docs/reference/Data/DXL_EXPORT_PROPERTY)
---
