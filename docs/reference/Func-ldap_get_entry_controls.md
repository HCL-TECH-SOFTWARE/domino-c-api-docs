##### Function : LDAP
##### ldap_get_entry_controls - Extract LDAP controls from an entry.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_get_entry_controls(**

	LDAP *ld,
	LDAPMessage *entry,
	LDAPControl ***ctrls);
**Description :**
This function is is used to extract LDAP controls from an entry.

Implemented as a macro:

#define ldap_get_entry_controls(ld, entry, ctrls) 
ND_ldap_get_entry_controls((ld), (entry), (ctrls))
**Parameters :**
Input :
ld  -  The LDAP session handle.

entry  -  The entry to extract controls from, as returned by ldap_first_entry or ldap_next_entry.

Output :
(routine)  -  LDAP_SUCCESS  - If the controls are successfully returned, or another LDAP result code if the value of the controls are undefined.


ctrls  -  An allocated array of controls copied out of the entry. The control array  SHOULD be freed by calling ldap_controls_free.  NULL, if no controls were returned.

**See Also :**
[ldap_control_free](D:/md_files/ldap_control_free.md)
[ldap_first_entry](D:/md_files/ldap_first_entry.md)
[ldap_next_entry](D:/md_files/ldap_next_entry.md)
---
