##### Data Type : SSO
##### SSO_LTPA2_ATTR - Structure to store info found in the LtpaToken2 data area.
---
```
#include <bsafe.h>
```

**Definition :**

typedef struct{     /* Structure to store info found */
	     /* in the LtpaToken2 data area.     */
	MEMHANDLE     mhSelf;
	MEMHANDLE mhKey;
	char	 *pKey;         /* locked pointer to key */
	DWORD  dwKeyLength;
	MEMHANDLE mhValue;
	char	 *pValue;  /* locked pointer to value */
	DWORD  dwValueLength;
	void	 *pNext;             /* struct SSO_LTPA2_ATTR  * pointer */
	}
	SSO_LTPA2_ATTR;


**Description :**

Structure to store info found in the LtpaToken2 data area.


**See Also :**
---
