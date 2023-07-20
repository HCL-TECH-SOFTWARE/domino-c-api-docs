##### Data Type : SSO
##### SSO_TOKEN_INFO_DESC - Structure to describe info found in the SSO token.
---
```
#include <bsafe.h>
```

**Definition :**
```
typedef struct{         /* Structure to describe info found */
	          /* in the SSO token. */
	DWORD   dwStructVersion;        /* currently must be set to 0 */
	DWORD   dwTokenVersion;         /* currently not used */
	SECTOKENFORMAT TokenType;
	SSO_TOKEN_ITEM Username;
	SSO_TOKEN_ITEM RawTokenUsername;
	TIMEDATE  Creation;
	TIMEDATE  Expiration;
	SSO_LTPA2_ATTR  *AttributesList;
	void	  *vpReservedTiming;
	void	  *vpReserved;
	}
	SSO_TOKEN_INFO_DESC;

```

**Description :**

<tt>Structure to describe info found in the SSO token.</tt>


**See Also :**
---
