##### Data Type : nao
##### NAO_OUTLINE_INFO - Outline infomation structure
---
```
#include <addinout.h>
```

**Definition :**
```
typedef struct
{
	DWORD    dwSize;     /* Size of this structure */
	char    szName[DESIGN_FORM_MAX];  /* Outline name */
	char    szAlias[DESIGN_FORM_MAX];  /* Outline alias */
	DBHANDLE   hDb;     /* Handle to current Db */
	BOOL    bExtendOutline;    /* Indicates whether or not to extend 
outline */
	DWORD    dwReserved1;    /* Reserved */
	DWORD    dwReserved2;    /* Reserved */
} NAO_OUTLINE_INFO;
```

**Description :**

Outline infomation structure.


**See Also :**
---
