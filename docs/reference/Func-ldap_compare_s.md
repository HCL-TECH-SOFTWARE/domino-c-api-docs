##### Function : LDAP
##### ldap_compare_s - Synchronous compare attribute value assertion
---
##### #include <ldap.h>
int LNPUBLIC **ldap_compare_s(**

	LDAP *ld,
	const char *dn,
	const char *attr,
	const char *value);
**Description :**
This function will do a synchronous compare attribute value assertion against 
an LDAP entry.

Implemented as a macro:

#define ldap_compare_s(ld, dn, attr, value) ND_ldap_compare_s((ld), (dn), 
(attr), (value))
**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to compare against.

attr  -  The attribute to compare against.

value  -  A string attribute value to compare against.

Output :
(routine)  -  LDAP_COMPARE_TRUE, LDAP_COMPARE_FALSE  - If the operation was successful, or another LDAP result code if not.


**Sample Usage :**
```
ldap_compare_s( ld, "CN = John Q Public, O = API", "userPassword", "secret" );
```
**See Also :**
[](D:/md_files/.md)
---
