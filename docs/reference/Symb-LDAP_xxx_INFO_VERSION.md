##### Symbolic Value : LDAP
##### LDAP_xxx_INFO_VERSION - LDAP execution information.
---
##### #include <ldap.h>
**Description :**
When LDAP_OPT_API_INFO is passed to ldap_get_option (see ldap_get_option and 
LDAP_OPT_xxx), the ldapai_info_version field of the LDAPAPIInfo or 
LDAPAPIFeatureInfo structures SHOULD be set to one of the appropriate values 
below, before calling ldap_get_option so that it can be checked for 
consistency.  
**See Also :**
[LDAPAPIFeatureInfo](D:/md_files/LDAPAPIFeatureInfo.md)
[LDAPAPIInfo](D:/md_files/LDAPAPIInfo.md)
[ldap_get_option](D:/md_files/ldap_get_option.md)
[LDAP_OPT_xxx](D:/md_files/LDAP_OPT_xxx.md)
---
