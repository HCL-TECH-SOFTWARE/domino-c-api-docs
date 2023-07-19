##### Data Type : XML
##### DXL_RICHTEXT_OPTION - DXL export richtext options
---
```
#include <xml.h>
```

**Definition :**

typedef enum
{
	eRichtextAsDxl,   /* (default) output richtext as dxl with warning 
	        comments if uninterpretable CD records */
	eRichtextAsItemdata  /* output richtext as uninterpretted (base64'ed) 
item data */

} DXL_RICHTEXT_OPTION;

**Description :**

Values to set DXL_EXPORT_PROPERTY member eDxlRichtextOption.  Default value is eRichtextAsDxl.


**See Also :**
[DXL_EXPORT_PROPERTY](/domino-c-api-docs/reference/Data/DXL_EXPORT_PROPERTY)
---
