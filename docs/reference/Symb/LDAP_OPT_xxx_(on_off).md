##### Symbolic Value : LDAP
##### LDAP_OPT_xxx (on/off) - LDAP library automatic referral control.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_OPT_ON	  -  LDAP library automatically controls referrals

	LDAP_OPT_OFF	  -  LDAP library does not automatically control referrals


**Description :**

LDAP_OPT_REFERRALS controls whether the LDAP library automatically controls referrals (LDAP_OPT_ON) or not (LDAP_OPT_OFF).


**See Also :**
[ldap_get_option](/domino-c-api-docs/reference/Func/ldap_get_option)
[LDAP_OPT_xxx](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx)
[LDAP_OPT_xxx (on/off)](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx (on/off))
[LDAP_OPT_xxx (SSL)](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx (SSL))
[ldap_set_option](/domino-c-api-docs/reference/Func/ldap_set_option)
---
