##### Symbolic Value : LDAP
##### LDAP_DEBUG_API - LDAP debug option.
---
```
#include <ldap.h>
```

**Symbolic Values :**



**Description :**

This is the value  for LDAP_OPT_DEBUG_LEVEL which can be set using the ldap_set_option function.  Setting this option will cause the ldap api debug information to be written out to the screen, and to a log file by specifying &quot;DEBUG_OUTFILE=&quot; and &quot;LDAPDEBUG=1&quot; parameters in the notes.ini.


**Sample Usage :**
```
WORD  ldap_debug_level = 0;

ldap_debug_level = LDAP_DEBUG_API;
ldap_set_option (NULL, LDAP_OPT_DEBUG_LEVEL, &ldap_debug_level);
```

**See Also :**
[LDAP_OPT_xxx](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx)
[ldap_set_option](/domino-c-api-docs/reference/Func/ldap_set_option)
---
