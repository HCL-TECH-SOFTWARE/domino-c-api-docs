##### Function : LDAP
##### ldap_value_free_len - Free the values retrieved by ldap_get_values_len.
---
##### #include <ldap.h>
void LNPUBLIC **ldap_value_free_len(**

	struct berval **vals);
**Description :**
This function is used to free the values retreived by ldap_get_values.

Implemented as a macro:

#define ldap_value_free_len(vals) ND_ldap_value_free_len((vals))
**Parameters :**
Input :
vals  -  The values returned by a previous call to ldap_get_values_len.  If a NULL is passed, nothing is done.


**See Also :**
[ldap_get_values_len](D:/md_files/ldap_get_values_len.md)
---
