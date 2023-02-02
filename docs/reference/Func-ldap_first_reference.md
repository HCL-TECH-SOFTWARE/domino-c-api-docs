##### Function : LDAP
##### ldap_first_reference - Get the first reference in the list of references.
---
##### #include <ldap.h>
LDAPMessage * LNPUBLIC **ldap_first_reference(**

	LDAP *ld,
	LDAPMessage *chain);
**Description :**
This function gets the first reference in the list of references in a result 
chain returned by ldap_result.  For search operations, the result chain can 
actually include referral messages, entry messages, and result messages.

Implemented as a macro:

#define ldap_first_reference(ld, chain) ND_ldap_first_reference((ld), (chain)) 
**Parameters :**
Input :
ld  -  The LDAP session handle.

chain  -  The result chain, as obtained by a call to one of the synchronous search routines or ldap_result.

Output :
(routine)  -  Pointer to the first reference in a chain of references.

NULL  - When no more references exist in the result set to be returned or if an error occurs while stepping through the entries, in which
case the error parameters in the session handle ld will be set to indicate the error.


**Sample Usage :**
```
ref = ldap_first_reference(ld, chain);
```
**See Also :**
[ldap_count_references](D:/md_files/ldap_count_references.md)
[ldap_next_reference](D:/md_files/ldap_next_reference.md)
[ldap_result](D:/md_files/ldap_result.md)
---
