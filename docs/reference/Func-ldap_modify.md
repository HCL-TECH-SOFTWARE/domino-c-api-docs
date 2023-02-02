##### Function : LDAP
##### ldap_modify - Asynchronously modify an existing LDAP entry.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_modify(**

	LDAP *ld,
	const char *dn,
	LDAPMod **mods);
**Description :**
This function initiates an asynchronous modify operation and returns the 
message id of the operation initiated.

Implemented as a macro:

#define ldap_modify(ld, dn, mods) ND_ldap_modify((ld), (dn), (mods))
**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to modify.  If NULL, a zero length DN is sent to the server.

mods  -  List of modifications to make.  This is null-terminated array of struct ldapmod's, specifying the modifications to perform.

Output :
(routine)  -  Message ID - This ID can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.

-1 - If an error occurs.


**Sample Usage :**
```
LDAPMod *mods[] = { 
                         { LDAP_MOD_ADD, "cn", { "babs jensen", "babs", 0 } },
                         { LDAP_MOD_REPLACE, "sn", { "jensen", 0 } },
                         0
                                      }

msgid = ldap_modify( ld, dn, mods );
```
**See Also :**
[LDAPMod](D:/md_files/LDAPMod.md)
---
