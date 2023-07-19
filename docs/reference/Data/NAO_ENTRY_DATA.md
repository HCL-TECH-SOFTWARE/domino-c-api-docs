##### Data Type : nao
##### NAO_ENTRY_DATA - Entry data structure
---
```
#include <addinout.h>
```

**Definition :**

typedef struct
{
	DWORD    dwSize;     /* Size of this structure */
	char    szName[DESIGN_NAME_MAX];  /* Outline entry name, full title or 
named element */
	DWORD    dwID;     /* Outline entry ID */
	DWORD    dwParentID;    /* ID of parent outline entry */
	DWORD    dwRefID;    /* Outline reference ID, only used by DLL 
implementation */
	DWORD    dwSecRefID;    /* Outline reference ID, only used by DLL 
implementation */
	DWORD    dwReserved1;    /* Reserved */
	DWORD    dwReserved2;    /* Reserved */
} NAO_ENTRY_DATA;

**Description :**

Entry data structure


**See Also :**
---
