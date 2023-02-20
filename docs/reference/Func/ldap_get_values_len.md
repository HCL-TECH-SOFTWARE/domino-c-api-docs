##### Function : LDAP
##### ldap_get_values_len - Retrieve the values of a given attribute.
---
```
#include <ldap.h>
struct berval **LNPUBLIC ldap_get_values_len(

	LDAP *ld,
	LDAPMessage *entry,
	const char *target);
```
**Description :**

This function is used to retrieve the values of a given attribute from an entry 
and is suitable for use with any kind of data.

Note that the values returned are dynamically allocated and SHOULD be freed by 
calling ldap_value_free_len when no longer in use.

Implemented as a macro:

#define ldap_get_values_len(ld, entry, target) ND_ldap_get_values_len((ld), 
(entry), (target))

**Parameters :**
Input :
ld  -  The LDAP session handle.

entry  -  The entry from which to retrieve values, as returned by ldap_first_entry or ldap_next_entry.

target  -  The attribute whose values are to be retrieved, as returned by ldap_first_attribute or ldap_next_attribute, or a caller supplied string (e.g., "mail").

Output :
(routine)  -  A pointer to a berval structure containing the given attribute values.

NULL - If no values are found or if an error occurs.



**See Also :**
[ldap_count_values](/reference/Func/ldap_count_values)
[ldap_count_values_len](/reference/Func/ldap_count_values_len)
[ldap_first_attribute](/reference/Func/ldap_first_attribute)
[ldap_first_entry](/reference/Func/ldap_first_entry)
[ldap_get_values](/reference/Func/ldap_get_values)
[ldap_next_attribute](/reference/Func/ldap_next_attribute)
[ldap_next_entry](/reference/Func/ldap_next_entry)
[ldap_value_free](/reference/Func/ldap_value_free)
[ldap_value_free_len](/reference/Func/ldap_value_free_len)
---
