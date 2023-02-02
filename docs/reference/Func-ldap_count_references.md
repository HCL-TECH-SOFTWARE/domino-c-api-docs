##### Function : LDAP
##### ldap_count_references - Get the number of references contained in a chain of results.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_count_references(**

	LDAP *ld,
	LDAPMessage *chain);
**Description :**
This function returns the number of references contained in a chain of 
results.  This can also be used to count the number of references that remain 
in a chain if called with a reference returned by ldap_first_reference or 
ldap_next_reference.

Implemented as a macro:

#define ldap_count_references(ld, chain) ND_ldap_count_references((ld), 
(chain))
**Parameters :**
Input :
ld  -  The LDAP session handle.

chain  -  The result chain, as obtained by a call to one of the synchronous search routines or ldap_result.

Output :
(routine)  -  rCount - The number of references  contained in a chain of results.

0 - No more references.

-1 - An error occured, such as the chain parameter being invalid.


**Sample Usage :**
```
rCount = ldap_count_references(Id, chain);
```
**See Also :**
[ldap_first_reference](D:/md_files/ldap_first_reference.md)
[ldap_next_message](D:/md_files/ldap_next_message.md)
[ldap_result](D:/md_files/ldap_result.md)
---
