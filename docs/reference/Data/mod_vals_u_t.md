##### Data Type : LDAP
##### mod_vals_u_t - Modify an existing LDAP entry.
---
```
#include <ldap.h>
```

**Definition :**
```
typedef union mod_vals_u
{
	char   **modv_strvals;
	struct berval **modv_bvals;
} mod_vals_u_t;
```

**Description :**

This union is used to modify an existing LDAP entry.


**See Also :**
---
