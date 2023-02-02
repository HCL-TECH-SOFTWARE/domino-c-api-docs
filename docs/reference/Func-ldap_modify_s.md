##### Function : LDAP
##### ldap_modify_s - Synchronously modify an existing LDAP entry.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_modify_s(**

	LDAP *ld,
	const char *dn,
	LDAPMod **mods);
**Description :**
This function initiates a synchronous modify operation.

Implemented as a macro:

#define ldap_modify_s(ld, dn, mods)  ND_ldap_modify_s((ld), (dn), (mods))
**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to modify.  If NULL, a zero length DN is sent to the server.

mods  -  List of modifications to make.  This is null-terminated array of struct ldapmod's, specifying the modifications to perform.

Output :
(routine)  -  LDAP_SUCCESS  - If the operation was successful, or another LDAP result code if not.


**Sample Usage :**
```
LDAPMod *mods[] = { 
                         { LDAP_MOD_ADD, "cn", { "babs jensen", "babs", 0 } },
                         { LDAP_MOD_REPLACE, "sn", { "jensen", 0 } },
                         0
                                      }

ldap_modify_s( ld, dn, mods );
```
**See Also :**
[LDAPMod](D:/md_files/LDAPMod.md)
---
