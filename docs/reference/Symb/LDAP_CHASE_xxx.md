##### Symbolic Value : LDAP
##### LDAP_CHASE_xxx - Flags for referrals client control value.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_CHASE_SUBORDINATE_REFERRALS	  -  LDAPv3 search continuation references are to be automatically chased. See LDAPControl.

	LDAP_CHASE_EXTERNAL_REFERRALS	  -  LDAPv3 referrals are to be automatically chased. See LDAPControl.


**Description :**

Flags for referrals client control value.  These flags can be combined to indicate that both referrals and references are to be automatically chased.


**See Also :**
[LDAPControl](/domino-c-api-docs/reference/Data/LDAPControl)
---
