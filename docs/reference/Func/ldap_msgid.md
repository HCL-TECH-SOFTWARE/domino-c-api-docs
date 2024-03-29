##### Function : LDAP
##### ldap_msgid - Return the message ID associated with the LDAP message.
---
```
#include <ldap.h>
int LNPUBLIC ldap_msgid(

	LDAPMessage *lm);
```
**Description :**

This function returns the message ID associated with the LDAP message passed as 
a parameter.

Implemented as a macro:

#define ldap_msgid(lm) ND_ldap_msgid((lm)) 

**Parameters :**
Input :
lm  -  The result of an operation.    See ldap_result.

Output :
(routine)  -  Message ID - Upon successful completion, returns the message ID associated with an LDAP message.

-1 - If an error occurs.



**Sample Usage :**
```
msgid = ldap_msgid(lm);
```
**See Also :**
[ldap_msgfree](/domino-c-api-docs/reference/Func/ldap_msgfree)
[ldap_msgtype](/domino-c-api-docs/reference/Func/ldap_msgtype)
[ldap_result](/domino-c-api-docs/reference/Func/ldap_result)
---
