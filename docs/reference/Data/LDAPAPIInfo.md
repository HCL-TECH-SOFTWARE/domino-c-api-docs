##### Data Type : LDAP
##### LDAPAPIInfo - LDAP structure containing LDAP API information.
---
```
#include <ldap.h>
```

**Definition :**

typedef struct ldapapiinfo {
	int  ldapai_info_version;     /* version of this struct (1) */
	int  ldapai_api_version;      /* revision of API supported */
	int  ldapai_protocol_version; /* highest LDAP version supported */
	char **ldapai_extensions;     /* names of API extensions */
	char *ldapai_vendor_name;     /* name of supplier */
	int  ldapai_vendor_version;   /* supplier-specific version times 100 */
} LDAPAPIInfo;

**Description :**

LDAP structure containing some basic information about the LDAP API and about the specific implementation being used.
<ul><br>
<br>
The function ldap_get_option can be used with an option parameter value of LDAP_OPT_API_INFO to retrieve this basic information about the LDAP API.  The ld parameter to ldap_get_option can be either NULL or a valid LDAP session handle which was obtained by calling ldap_init.  When LDAP_OPT_API_INFO is passed to ldap_get_option, the option value returned SHOULD be the address of an LDAPAPIInfo structure.<br>
<br>
Note that the ldapai_info_version field of the LDAPAPIInfo structure SHOULD be set to the value LDAP_API_INFO_VERSION before calling ldap_get_option so that it can be checked for consistency.  All other fields are set by the ldap_get_option function.<br>
<br>
The members of the LDAPAPIInfo structure are:<br>
<br>
ldapai_info_version		- A number that identifies the version of the LDAPAPIInfo structure.  This SHOULD be set to the value LDAP_API_INFO_VERSION before calling ldap_get_option.  If the value received is not recognized by the API implementation, the ldap_get_option function sets ldapai_info_version to a valid value that would be recognized, sets the ldapai_api_version to the correct value, and returns an error without filling in any of the other fields in the LDAPAPIInfo structure.<br>
<br>
ldapai_api_version		- A number that matches that assigned to the C LDAP API RFC supported by the API implementation.  This SHOULD match the value of the LDAP_API_VERSION macro defined earlier.<br>
<br>
ldapai_protocol_version	- The highest LDAP protocol version supported by the implementation.  For example, if LDAPv3 is the highest version supported then this field will be set to 3.<br>
<br>
ldapai_vendor_name	- A zero-terminated string that contains the name of the party that produced the LDAP API implementation.  This field may be set to NULL if no name is available.  If non-NULL, the caller  is responsible for disposing of the memory occupied by passing this pointer to ldap_memfree.<br>
This value SHOULD match the value of the LDAP_VENDOR_NAME.  See LDAP_VENDOR_xxx.<br>
<br>
ldapai_vendor_version	- An implementation-specific version number multiplied by 100.  For example, if the implementation version is 4.0 then this field will be set to 400.  If no version information is available, this field will be set to 0.  This value SHOULD match the value of the LDAP_VENDOR_VERSION.  See LDAP_VENDOR_xxx.</ul>



**See Also :**
[ldap_get_option](/domino-c-api-docs/reference/Func/ldap_get_option)
[LDAP_VENDOR_xxx](/domino-c-api-docs/reference/Symb/LDAP_VENDOR_xxx)
[LDAP_xxx_INFO_VERSION](/domino-c-api-docs/reference/Symb/LDAP_xxx_INFO_VERSION)
---
