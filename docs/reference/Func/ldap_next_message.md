##### Function : LDAP
##### ldap_next_message - Get the next message in the list of messages.
---
```
#include <ldap.h>
LDAPMessage * LNPUBLIC ldap_next_message(

	LDAP *ld,
	LDAPMessage *msg);
```
**Description :**

This function gets the next message in the list of messages in a result chain 
returned by ldap_result.  For search operations, the result chain can actually 
include referral messages, entry messages, and result messages.

Implemented as a macro:

#define ldap_next_message(ld, msg) ND_ldap_next_message((ld), (msg))

**Parameters :**
Input :
ld  -  The LDAP session handle.

msg  -  The message returned by a previous call to ldap_first_message or ldap_next_message.

Output :
(routine)  -  Pointer to the next message of a message chain.

NULL  - When no more messages exist in the result set to be returned or if an error occurs while stepping through the entries, in which
case the error parameters in the session handle ld will be set to indicate the error.



**Sample Usage :**
```
nmsg = ldap_next_message(ld, msg);
```
**See Also :**
[ldap_count_messages](/reference/Func/ldap_count_messages)
[ldap_first_message](/reference/Func/ldap_first_message)
---
