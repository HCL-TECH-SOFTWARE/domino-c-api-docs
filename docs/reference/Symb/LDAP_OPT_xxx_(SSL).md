##### Symbolic Value : LDAP
##### LDAP_OPT_xxx (SSL) - LDAP options.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_OPT_REFERRALS	  -  Determines whether the LDAP library automatically follows referrals returned by LDAP servers or not. It MAY be set to one of the constants LDAP_OPT_ON or LDAP_OPT_OFF (see LDAP_OPT_xxx(on/off)); any non-NULL pointer value passed to ldap_set_option enables this option. When reading the current setting using ldap_get_option, a zero value means OFF and any non-zero value means ON. By default, this option is ON. Set optionValue type to int * for ldap_get_option. Set optionValue type to void * (LDAP_OPT_ON or LDAP_OPT_OFF) for ldap_set_option.

	LDAP_OPT_RESTART	  -  Determines whether LDAP I/O operations are automatically restarted if they abort prematurely. It MAY be set to one of the constants LDAP_OPT_ON or LDAP_OPT_OFF (see LDAP_OPT_xxx(on/off)); any non-NULL pointer value passed to ldap_set_option() enables this option. When reading the current setting using ldap_get_option, a zero value means OFF and any non-zero value means ON. This option is useful if an LDAP I/O operation can be interrupted prematurely, for example by a timer going off, or other interrupt. By default, this option is OFF. Set optionValue type to int * for ldap_get_option. Set optionValue type to void * (LDAP_OPT_ON or LDAP_OPT_OFF) for ldap_set_option.

	LDAP_OPT_SSL	  -  Use SSL for client connections.


**Description :**

LDAP options that can be accessed or set using the functions ldap_get_option and ldap_set_option.  Type may differ dependant on whether option is to be accessed or set.


**See Also :**
[ldap_get_option](/domino-c-api-docs/reference/Func/ldap_get_option)
[LDAP_OPT_xxx](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx)
[LDAP_OPT_xxx (on/off)](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx (on/off))
[LDAP_OPT_xxx (SSL)](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx (SSL))
[ldap_set_option](/domino-c-api-docs/reference/Func/ldap_set_option)
---
