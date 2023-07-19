##### Data Type : nao
##### NAO_ENTRY_INFO - Entry infomation structure
---
```
#include <addinout.h>
```

**Definition :**

typedef struct
{
	DWORD    dwSize;     /* Size of this structure */
	NAO_ENTRY_DATA   EntryData;    /* NAO_ENTRY_DATA */
	NAO_ENTRY_RESOURCE  EntryResource;    /* NAO_ENTRY_RESOURCE */
	WORD    wEntryResourceType;   /* NAO_RESOURCE_XXX */
	NAO_IMAGE_DATA   ImageData;    /* NAO_IMAGE_DATA */
	DWORD    dwReserved1;    /* Reserved */
	DWORD    dwReserved2;    /* Reserved */
} NAO_ENTRY_INFO;

**Description :**

Entry infomation structure.


**See Also :**
---
