##### Function : LDAP
##### ldap_compare - Asynchronous compare attribute value assertion
---
```
#include <ldap.h>
int LNPUBLIC ldap_compare(

	LDAP *ld,
	const char *dn,
	const char *attr,
	const char *value);
```
**Description :**

This function will do an asynchronous compare attribute value assertion against 
an LDAP entry.

Implemented as a macro:

#define ldap_compare(ld, dn, attr, value) ND_ldap_compare((ld), (dn), (attr), 
(value)) 

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to compare against.

attr  -  The attribute to compare against.

value  -  A string attribute value to compare against.

Output :
(routine)  -  Message ID - This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.

-1 - If an error occurs.



**Sample Usage :**
```
ldap_compare( ld, "CN = John Q Public, O = API", "userPassword", "secret" );
```
**See Also :**
---
