##### Function : LDAP
##### ldap_control_free - Dispose of a single control.
---
##### #include <ldap.h>
void LNPUBLIC **ldap_control_free(**

	LDAPControl *ctrl);
**Description :**
This function is used to dispose of a single control.

Implemented as a macro:

#define ldap_control_free(ctrl) ND_ldap_control_free((ctrl))
**Parameters :**
Input :
ctrl  -  Pointer to an LDAPControl structure.  See LDAPControl.  If NULL, this call does nothing.


**See Also :**
[](D:/md_files/.md)
---
