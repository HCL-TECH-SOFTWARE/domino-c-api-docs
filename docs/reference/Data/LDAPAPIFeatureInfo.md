##### Data Type : LDAP
##### LDAPAPIFeatureInfo - LDAP structure containing LDAP API feature information.
---
```
#include <ldap.h>
```
**Description :**

LDAP structure containing some feature information about the LDAP API.

The function ldap_get_option can be used with an option parameter value of 
LDAP_OPT_API_FEATURE_INFO to retrieve more feature information about the LDAP 
API.  When LDAP_OPT_API_FEATURE_INFO is passed to ldap_get_option, the option 
value returned SHOULD be the address of an LDAPAPIFeatureInfo structure.

Note that the ldapaif_info_version field of the LDAPAPIFeatureInfo structure 
SHOULD be set to the value LDAP_FEATURE_INFO_VERSION and the ldapaif_name field 
SHOULD be set to the extension name string as described below before 
ldap_get_option is called.  When LDAP_OPT_API_FEATURE_INFO is passed to 
ldap_get_option, the  value returned for the ldapaif_version  field of the 
LDAPAPIFeatureInfo structure will be set.

The members of the LDAPAPIFeatureInfo structure are:

ldapaif_info_version - A number that identifies the version of the 
LDAPAPIFeatureInfo structure.  This SHOULD be set to the value           
LDAP_FEATURE_INFO_VERSION before calling ldap_get_option.  If the value 
received is not recognized by the LDAP API implementation, the ldap_get_option 
function sets ldapaif_info_version to a valid value that would be recognized 
and returns an error without filling in the ldapaif_version field in the 
LDAPAPIFeatureInfo structure.

ldapaif_name  - The name of an extension, as returned in the ldapai_extensions 
array of the LDAPAPIInfo structure and as specified in the document that 
describes the extension.  See LDAPAPIInfo.

ldapaif_version  - This field will be set as a result of calling 
ldap_get_option with the LDAP_OPT_API_FEATURE_INFO option.

**See Also :**
[LDAPAPIInfo](/domino-c-api-docs/reference/Data/LDAPAPIInfo)
[ldap_get_option](/domino-c-api-docs/reference/Func/ldap_get_option)
[LDAP_xxx_INFO_VERSION](/domino-c-api-docs/reference/Symb/LDAP_xxx_INFO_VERSION)
---
