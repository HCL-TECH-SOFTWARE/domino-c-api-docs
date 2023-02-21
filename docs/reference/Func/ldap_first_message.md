##### Function : LDAP
##### ldap_first_message - Get the first message in the list of messages.
---
```
#include <ldap.h>
LDAPMessage * LNPUBLIC ldap_first_message(

	LDAP *ld,
	LDAPMessage *res);
```
**Description :**

This function gets the first message in the list of messages in a result chain 
returned by ldap_result.  For search operations, the result chain can actually 
include referral messages, entry messages, and result messages.

Implemented as a macro:

#define ldap_first_message(ld, res)  ND_ldap_first_message((ld), (res))

**Parameters :**
Input :
ld  -  The LDAP session handle.

res  -  The result chain, as obtained by a call to one of the synchronous search routines or ldap_result.

Output :
(routine)  -  Pointer to the first message of a message chain.

NULL  - When no more messages exist in the result set to be returned or if an error occurs while stepping through the entries, in which
case the error parameters in the session handle ld will be set to indicate the error.



**Sample Usage :**
```
msg = ldap_first_message(ld, res);
```
**See Also :**
[ldap_count_messages](/domino-c-api-docs/reference/Func/ldap_count_messages)
[ldap_next_message](/domino-c-api-docs/reference/Func/ldap_next_message)
[ldap_result](/domino-c-api-docs/reference/Func/ldap_result)
---
