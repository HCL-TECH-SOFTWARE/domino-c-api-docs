##### Data Type : SSO
##### SSO_LTPA_TOKEN_LIST - Structure to store returned Ltpa tokens in a list.
---
```
#include <bsafe.h>
```

**Definition :**

typedef struct{         /* Structure to store returned Ltpa tokens in a list. 
*/     
	MEMHANDLE     mhSelf;   /* Memory allocated for this struct */
	SECTOKENFORMAT    TokenType;
	MEMHANDLE     mhToken;
	SSO_TOKEN     *pToken;         /* locked pointer to token allocated in 
mhToken */
	void      *pNext;   /* struct SSO_LTPA_TOKEN_LIST * to next struct in 
list */
	}
	SSO_LTPA_TOKEN_LIST;


**Description :**

Structure to store returned Ltpa tokens in a list.


**See Also :**
---
