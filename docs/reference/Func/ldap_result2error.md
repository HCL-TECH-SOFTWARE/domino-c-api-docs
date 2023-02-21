##### Function : LDAP
##### ldap_result2error - Return an error code from an LDAP result message.
---
```
#include <ldap.h>
int LNPUBLIC ldap_result2error(

	LDAP *ld,
	LDAPMessage *r,
	int  freeit);
```
**Description :**

This function returns an error code from an LDAP result message.

Implemented as a macro:

#define ldap_result2error(ld, r, freeit)  ND_ldap_result2error((ld), (r), 
(freeit)) 

**Parameters :**
Input :
ld  -  The LDAP session handle.

r  -  The result of an LDAP operation as returned by ldap_result or one of the synchronous API operation calls.

freeit  -  A boolean that determines whether the result parameter is  disposed of or not.  If freeit is non-zero, the entire chain of messages represented by result is disposed of after extracting the requested information. This is provided as a convenience; zero can also be passed, to not free the messages, and ldap_msgfree can be used to free the result later.

Output :
(routine)  -  LDAP error code.



**Sample Usage :**
```
err = ldap_result2error(Id, r, 1);
```
**See Also :**
[ldap_err2string](/domino-c-api-docs/reference/Func/ldap_err2string)
---
