##### Data Type : LDAP
##### LDAPMod - Modify an existing LDAP entry.
---
```
#include <ldap.h>
```

**Definition :**

typedef struct ldapmod 
{

	int    mod_op;

#define LDAP_MOD_ADD  0x00
#define LDAP_MOD_DELETE 0x01
#define LDAP_MOD_REPLACE 0x02
#define LDAP_MOD_BVALUES 0x80

	char   *mod_type;
	mod_vals_u_t mod_vals;

#define mod_values mod_vals.modv_strvals
#define mod_bvalues mod_vals.modv_bvals

	struct ldapmod *mod_next;

}  LDAPMod;

**Description :**

This structure is used to modify an existing LDAP entry.


**See Also :**
[LDAP_MOD_xxx](/domino-c-api-docs/reference/Symb/LDAP_MOD_xxx)
---
