##### Function : LDAP
##### ldap_count_messages - Get the number of messages contained in a chain of results.
---
```
#include <ldap.h>
int LNPUBLIC ldap_count_messages(

	LDAP *ld,
	LDAPMessage *res);
```
**Description :**

This function returns the number of messages contained in a chain of results.  
This can also be used to count the number of messages that remain in a chain if 
called with a message returned by ldap_first_message or ldap_next_message.

Implemented as a macro:

#define ldap_count_messages(ld, res) ND_ldap_count_messages((ld), (res))

**Parameters :**
Input :
ld  -  The LDAP session handle.

res  -  The result chain, as obtained by a call to one of the synchronous search routines or ldap_result.

Output :
(routine)  -  mCount - The number of messages  contained in a chain of results.

0 - No more messages.

-1 - An error occured, such as the res parameter being invalid.



**Sample Usage :**
```
mCount = ldap_count_messages(ld, res);
```
**See Also :**
[ldap_first_message](/reference/Func/ldap_first_message)
[ldap_next_message](/reference/Func/ldap_next_message)
---
