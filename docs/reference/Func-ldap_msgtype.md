##### Function : LDAP
##### ldap_msgtype - Returns the type of the LDAP message.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_msgtype(**

	LDAPMessage *lm);
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
[ldap_first_entry](D:/md_files/ldap_first_entry.md)
[ldap_first_message](D:/md_files/ldap_first_message.md)
[ldap_first_reference](D:/md_files/ldap_first_reference.md)
[ldap_msgfree](D:/md_files/ldap_msgfree.md)
[ldap_msgid](D:/md_files/ldap_msgid.md)
[ldap_next_entry](D:/md_files/ldap_next_entry.md)
[ldap_next_message](D:/md_files/ldap_next_message.md)
[ldap_next_reference](D:/md_files/ldap_next_reference.md)
[ldap_result](D:/md_files/ldap_result.md)
---
