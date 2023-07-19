##### Data Type : XML
##### DXL_MIME_OPTION - DXL export MIME options
---
```
#include <xml.h>
```

**Definition :**

typedef enum{
	eMimeAsDxl,    /* (default) output native MIME within <mime> element in 
DXL */
	eMimeAsItemdata   /* output MIME as uninterpretted (base64'ed) item 
data */

} DXL_MIME_OPTION;


**Description :**

<font color="#008000">DXL export MIME options</font>


**See Also :**
---
