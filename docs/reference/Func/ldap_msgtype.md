##### Function : LDAP
##### ldap_msgtype - Returns the type of the LDAP message.
---
```
#include <ldap.h>
int LNPUBLIC ldap_msgtype(

	LDAPMessage *lm);
```
**Description :**

This function returns the type of the LDAP message it is passed as a 
parameter.  It can be used to distinguish between the different message types: 
referral messages, entry messages, and result_messages.  See LDAP_RES_xxx.

Implemented as a macro:

#define ldap_msgtype(lm) ND_ldap_msgtype((lm))

**Parameters :**
Input :
lm  -  The result(s) of an operation.    See ldap_result.

Output :
(routine)  -  LDAP_RES_xxx - Upon successful completion, returns the LDAP message type.

-1 - If an error occurs.



**See Also :**
[ldap_first_entry](/reference/Func/ldap_first_entry)
[ldap_first_message](/reference/Func/ldap_first_message)
[ldap_first_reference](/reference/Func/ldap_first_reference)
[ldap_msgfree](/reference/Func/ldap_msgfree)
[ldap_msgid](/reference/Func/ldap_msgid)
[ldap_next_entry](/reference/Func/ldap_next_entry)
[ldap_next_message](/reference/Func/ldap_next_message)
[ldap_next_reference](/reference/Func/ldap_next_reference)
[ldap_result](/reference/Func/ldap_result)
---
