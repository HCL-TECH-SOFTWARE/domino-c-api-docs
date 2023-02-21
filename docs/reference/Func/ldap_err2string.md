##### Function : LDAP
##### ldap_err2string - Maps numerical error codes to character strings.
---
```
#include <ldap.h>
char *LNPUBLIC ldap_err2string(

	int  err);
```
**Description :**

This function is used to convert a numeric LDAP result code, as returned by 
ldap_parse_result or one of the synchronous API operation calls, into an 
informative zero-terminated character string message describing the error.  

Implemented as a macro:

#define ldap_err2string(err) ND_ldap_err2string((err)) 

**Parameters :**
Input :
err  -  LDAP result code, as returned by ldap_parse_result or another LDAP API call.

Output :
(routine)  -  A pointer to static data (it MUST NOT return NULL); the value returned is always a valid null-terminated "C" string.



**See Also :**
[ldap_parse_result](/domino-c-api-docs/reference/Func/ldap_parse_result)
---
