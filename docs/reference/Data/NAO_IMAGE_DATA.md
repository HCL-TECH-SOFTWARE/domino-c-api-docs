##### Data Type : nao
##### NAO_IMAGE_DATA - Image data structure
---
```
#include <addinout.h>
```

**Definition :**
```
typedef struct
{
	DWORD    dwSize;     /* Size of this structure */
	char    szName[DESIGN_NAME_MAX];  /* Image name */
	DBID    DbID;     /* Replica ID containing szImageName, if not current 
database */
	DBHANDLE   hDb;     /* Handle containing szImageName, if not current 
database and not on workspace */
	DWORD    dwReserved1;    /* Reserved */
	DWORD    dwReserved2;    /* Reserved */
} NAO_IMAGE_DATA;
```

**Description :**

Image data structure


**See Also :**
---
