##### Function : LDAP
##### ldap_count_values - Count the attribute entry values.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_count_values(**

	char **vals);
**Description :**
This function is used to count the number of attribute entry value strings in 
the array.

Implemented as a macro:

#define ldap_count_values(vals) ND_ldap_count_values((vals)) 
**Parameters :**
Input :
vals  -  The values returned by a previous call to ldap_get_values.

Output :
(routine)  -  Number of attribute entry value strings in the array.

-1 - If an error occurs such as an invalid input for values.


**See Also :**
[ldap_get_values](D:/md_files/ldap_get_values.md)
---
