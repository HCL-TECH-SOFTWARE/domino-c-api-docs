##### Data Type : LDAP
##### LDAPsortKey - LDAP sort key structure 
---
```
#include <ldap.h>
```

**Definition :**

typedef struct ldapsortkey {
	char *  attributeType;
	char *  orderingRule;
	int     reverseOrder;
} LDAPsortKey;

**Description :**

LDAP structure containing the information specified by the string representation of a sort key.


**See Also :**
---
