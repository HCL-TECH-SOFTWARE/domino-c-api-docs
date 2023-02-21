##### Function : LDAP
##### ldap_parse_sort_control - Decode the server-side sort control return information.
---
```
#include <ldap.h>
int LNPUBLIC ldap_parse_sort_control(

	LDAP *ld,
	LDAPControl **ctrls,
	unsigned long  *returnCode,
	char **attribute);
```
**Description :**

This function will decode the server-side sort control return information.

Implemented as a macro:

#define ldap_parse_sort_control(ld, ctrls, returnCode, attribute)\
	        ND_ldap_parse_sort_control((ld), (ctrls), (returnCode), 
(attribute))

**Parameters :**
Input :
ld  -  The LDAP session handle.

ctrls  -  The address of a NULL terminated array of LDAPControl structures, typically obtained by a call to ldap_parse_result.

Output :
(routine)  -  LDAP_SUCCESS  - If the sort control was successfully parsed, or another LDAP result code if not.


*returnCode  -  The sort control result code.  This parameter MUST not be NULL.

attribute  -  If an error occured the server may return a string indicating the first attribute in the sortkey list that was in error.  If a string is returned, the memory should be freed with ldap_memfree.  If NULL, no string is returned.


**See Also :**
[ldap_memfree](/domino-c-api-docs/reference/Func/ldap_memfree)
[ldap_parse_result](/domino-c-api-docs/reference/Func/ldap_parse_result)
---
