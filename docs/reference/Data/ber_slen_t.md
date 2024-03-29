##### Data Type : Basic Encoding Rules
##### ber_slen_t - Used for passing lengths to/from the API.
---
```
#include <lber.h>
```

**Definition :**
```
typedef long ber_slen_t;
```

**Description :**

The ber_slen_t type is the signed variant of the ber_len_t integral type. Note that ber_slen_t is not used directly in the LDAP C API but is provided for the convenience of application developers and for use by extensions to the API.


**See Also :**
[ber_len_t](/domino-c-api-docs/reference/Data/ber_len_t)
---
