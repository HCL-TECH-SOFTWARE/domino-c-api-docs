##### Function : LDAP
##### ldap_controls_free - Dispose of an array of controls.
---
##### #include <ldap.h>
void LNPUBLIC **ldap_controls_free(**

	LDAPControl **ctrl);
**Description :**
This function is used to dispose of an array of controls.

Implemented as a macro:

#define ldap_controls_free(ctrl) ND_ldap_controls_free((ctrl))
**Parameters :**
Input :
ctrl  -  A pointer to a NULL terminated array of LDAPControl structures.  See LDAPControl.    If NULL, this call does nothing.


**See Also :**
[ldap_get_entry_controls](D:/md_files/ldap_get_entry_controls.md)
[ldap_parse_reference](D:/md_files/ldap_parse_reference.md)
---
