##### Symbolic Value : LDAP
##### LDAP_xxx_INFO_VERSION - LDAP execution information.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_API_INFO_VERSION	  -  A number that identifies the version of the LDAPAPIInfo structure. See LDAPAPIInfo.

	LDAP_FEATURE_INFO_VERSION	  -  A number that identifies the version of the LDAPAPIFeatureInfo structure. See LDAPAPIFeatureInfo.


**Description :**

When LDAP_OPT_API_INFO is passed to ldap_get_option (see ldap_get_option and LDAP_OPT_xxx), the ldapai_info_version field of the LDAPAPIInfo or LDAPAPIFeatureInfo structures SHOULD be set to one of the appropriate values below, before calling ldap_get_option so that it can be checked for consistency.  


**See Also :**
[LDAPAPIFeatureInfo](/domino-c-api-docs/reference/Data/LDAPAPIFeatureInfo)
[LDAPAPIInfo](/domino-c-api-docs/reference/Data/LDAPAPIInfo)
[ldap_get_option](/domino-c-api-docs/reference/Func/ldap_get_option)
[LDAP_OPT_xxx](/domino-c-api-docs/reference/Symb/LDAP_OPT_xxx)
---
