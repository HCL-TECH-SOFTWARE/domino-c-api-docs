##### Function : LDAP
##### ldap_next_reference - Get the next reference in the list of references.
---
```
#include <ldap.h>
LDAPMessage * LNPUBLIC ldap_next_reference(

	LDAP *ld,
	LDAPMessage *chain);
```
**Description :**

This function gets the next reference in the list of references in a result 
chain returned by ldap_result.  For search operations, the result chain can 
actually include referral messages, entry messages, and result messages.

Implemented as a macro:

#define ldap_next_reference(ld, chain) ND_ldap_next_reference((ld), (chain))

**Parameters :**
Input :
ld  -  The LDAP session handle.

chain  -  The message returned by a previous call to ldap_first_reference or ldap_next_reference.

Output :
(routine)  -  Pointer to the next reference in a chain of references.

NULL  - When no more references exist in the result set to be returned or if an error occurs while stepping through the entries, in which
case the error parameters in the session handle ld will be set to indicate the error.



**Sample Usage :**
```
nref = ldap_next_reference(ld, chain);
```
**See Also :**
[ldap_count_references](/domino-c-api-docs/reference/Func/ldap_count_references)
[ldap_first_reference](/domino-c-api-docs/reference/Func/ldap_first_reference)
[ldap_result](/domino-c-api-docs/reference/Func/ldap_result)
---
