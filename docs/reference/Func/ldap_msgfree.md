##### Function : LDAP
##### ldap_msgfree - Free each message in the result chain.
---
```
#include <ldap.h>
int LNPUBLIC ldap_msgfree(

	LDAPMessage *lm);
```
**Description :**

This function frees each message in the result chain and returns the type of 
the last message in the chain.  If result is NULL, nothing is done and the 
value zero is returned.  See LDAP_RES_xxx.

Implemented as a macro:

#define ldap_msgfree(lm) ND_ldap_msgfree((lm))  

**Parameters :**
Input :
lm  -  The result(s) of an operation.  See ldap_result.

Output :
(routine)  -  LDAP_RES_xxx - Upon successful completion, returns the LDAP message type.

0 - Result is NULL.

-1 - If an error occurs.



**See Also :**
[ldap_msgid](/domino-c-api-docs/reference/Func/ldap_msgid)
[ldap_msgtype](/domino-c-api-docs/reference/Func/ldap_msgtype)
[ldap_result](/domino-c-api-docs/reference/Func/ldap_result)
[LDAP_RES_xxx](/domino-c-api-docs/reference/Symb/LDAP_RES_xxx)
---
