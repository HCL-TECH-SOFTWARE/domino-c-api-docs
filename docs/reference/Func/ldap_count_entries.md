##### Function : LDAP
##### ldap_count_entries - Get the number of entries contained in a chain of results.
---
```
#include <ldap.h>
int LNPUBLIC ldap_count_entries(

	LDAP *ld,
	LDAPMessage *chain);
```
**Description :**

This function returns the number of entries contained in a chain of results.  
This can also be used to count the number of entries that remain in a chain if 
called with an entry, or reference returned by ldap_first_entry or 
ldap_next_entry.

Implemented as a macro:

#define ldap_count_entries(ld, chain) ND_ldap_count_entries((ld), (chain))

**Parameters :**
Input :
ld  -  The LDAP session handle.

chain  -  The result chain, as obtained by a call to one of the synchronous search routines or ldap_result.

Output :
(routine)  -  The number of entries  contained in a chain of results.

0 - No more entries.

-1 - An error occured, such as the chain parameter being invalid.



**Sample Usage :**
```
eCount = ldap_count_entries(Id, chain);
```
**See Also :**
[ldap_first_entry](/domino-c-api-docs/reference/Func/ldap_first_entry)
[ldap_next_entry](/domino-c-api-docs/reference/Func/ldap_next_entry)
[ldap_result](/domino-c-api-docs/reference/Func/ldap_result)
---
