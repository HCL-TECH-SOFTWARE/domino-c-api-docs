##### Data Type : LDAP
##### LDAPMessage - Represents ldap messages and ldap responses
---
```
#include <ldap.h>
```

**Definition :**
```
typedef struct ldapmsg LDAPMessage;
```

**Description :**

This structure represents both ldap messages and ldap responses. These are really the same, except in the case of search responses, where a response has multiple messages.


**See Also :**
---
