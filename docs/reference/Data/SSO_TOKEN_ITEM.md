##### Data Type : SSO
##### SSO_TOKEN_ITEM - Structure to store info found in the SSO token.
---
```
#include <bsafe.h>
```

**Definition :**
```
typedef struct{     /* Structure to store info found */
	      /* in the SSO token. */
	MEMHANDLE  mhItem;
	char   *ptr;
       DWORD   dwLength;
	}
	SSO_TOKEN_ITEM;

```

**Description :**

Structure to store info found in the SSO token.


**See Also :**
---
