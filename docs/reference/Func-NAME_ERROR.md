##### Function : LDAP
##### NAME_ERROR - Check for naming error.
---
##### #include <ldap.h>
Int **NAME_ERROR(**

	int  n);
**Description :**
This macro returns zero if the input is NOT one of the possible returned naming 
error codes and non-zero if it is.  See LDAP_xxx(1) 

This macro is defined as follows:

#define NAME_ERROR(n) ((n & 0xf0) == 0x20)
**Parameters :**
Input :
n  -  The result of an LDAP operation as returned by ldap_result or one of the synchronous API operation calls.

Output :
(routine)  -  Zero if the input is NOT one of the possible returned naming error codes and non-zero if it is.  


**See Also :**
[](D:/md_files/.md)
---
