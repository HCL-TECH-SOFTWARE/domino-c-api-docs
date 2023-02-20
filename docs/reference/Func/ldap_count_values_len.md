##### Function : LDAP
##### ldap_count_values_len - Count the number of berval structures.
---
```
#include <ldap.h>
int LNPUBLIC ldap_count_values_len(

	struct berval **vals);
```
**Description :**

This function is used to count the number of berval structures in the array.

Implemented as a macro:

#define ldap_count_values_len(vals) ND_ldap_count_values_len((vals))

**Parameters :**
Input :
vals  -  The values returned by a previous call to ldap_get_values_len.

Output :
(routine)  -  Number of berval structures in the array.

-1 - If an error occurs such as an invalid input for values.



**See Also :**
[ldap_get_values_len](/reference/Func/ldap_get_values_len)
---
